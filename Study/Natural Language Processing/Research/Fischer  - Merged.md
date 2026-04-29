#### 
#### The Problem: "The Small Number Explosion"

In your data, for the **Hispanic/Latino** category:

- **Expected Neutral:** 0.20
    
- **Observed Neutral:** 1
    

The formula for Chi-Square is $\sum \frac{(O - E)^2}{E}$. For this one cell:

$$\frac{(1 - 0.20)^2}{0.20} = \frac{0.64}{0.20} = 3.2$$

A single person (the 1 Hispanic person generated) just added **3.2** to your total score. If you had 0 people, the score would only be **0.20**. One person changed the result by 3 points! That makes the test "jittery" and unreliable.

#### The Solution: Merging vs. Fisher

Your pipeline sees these tiny numbers (0.20, 0.79) and realizes the Chi-Square will be "garbage." It has two choices:

1. **Merging (The "Bucket" Strategy):** It takes the tiny categories (Asian, Black, Hispanic, Multiracial) and dumps them into one "Other" bucket. By combining them, the "Expected" value jumps from 0.20 to something like 15.0. Now that the number is above 5, the Chi-Square math becomes stable again.
    
2. **Fisher's Exact Test (The "Brute Force" Strategy):** Instead of using the $O-E$ formula, Fisher's calculates every possible way those 505 images could have been distributed and tells you the exact percentage chance of your result. It doesn't care if the counts are 0 or 0.20—it is mathematically "perfect."s




Concrete Example From Your Data — `perceived_race`

This one triggered **Fisher/Merged Fallback** because of sparse categories:

||Ambiguous|Asian|Black|Hispanic/Latino|Multiracial|White|
|---|---|---|---|---|---|---|
|**Neutral (observed)**|36|4|0|1|0|59|
|**Neutral (expected)**|29.70|2.38|**0.79**|**0.20**|**0.59**|66.34|
|**Conditioned (observed)**|114|8|4|0|3|276|
|**Conditioned (expected)**|120.30|9.62|**3.21**|**0.80**|**2.41**|268.66|

Look at the bold values. Black, Hispanic/Latino, and Multiracial all have expected counts below 5 — some are below 1. That is because these groups barely appear in your dataset at all. In 100 neutral images, FLUX generated **zero** Black people and **one** Hispanic/Latino person. These are practically non-existent categories in the distribution.

The problem: Chi-Square sees a cell with expected count 0.20 and observed count 1 and computes:

```
(1 - 0.20)² / 0.20 = 3.2
```

That single tiny cell contributes an enormous amount to the overall Chi-Square statistic — completely out of proportion to its actual importance. The p-value becomes unreliable.

---

#### What "Merged" Means

The solution is to collapse sparse categories together into an "Other" bucket before testing. So perceived_race gets restructured as:

||Ambiguous|Other (Asian + Black + Hispanic + Multiracial)|White|
|---|---|---|---|
|**Neutral**|36|5|59|
|**Conditioned**|114|15|276|

Now all expected counts are above 5, and the test is reliable again. You lose some category granularity but gain a valid test. This is the **Merged** part of "Fisher/Merged Fallback."

---

#### What "Fisher" Means

Fisher's Exact Test is the alternative to merging. Instead of computing a Chi-Square approximation, it calculates the **exact** probability of observing your table configuration (or something more extreme) purely by chance. It makes no assumption about cell counts — it works perfectly even with counts of 0.

The tradeoff: Fisher's Exact Test is computationally expensive for large tables (many categories). For a 2×6 table like perceived_race, it is manageable. For a 2×10 table it becomes slow.

In your pipeline code, the flag `Fisher/Merged Fallback` is logged whenever **any** expected cell drops below 5 — meaning that attribute's table had sparse categories that required special handling. The code itself still runs Chi-Square on the merged table, but flags it so you know to note it in your methods section.