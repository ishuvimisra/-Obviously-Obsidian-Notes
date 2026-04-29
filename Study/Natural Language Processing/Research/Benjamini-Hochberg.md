The **Benjamini-Hochberg (BH) procedure** is a statistical method used to control the **False Discovery Rate (FDR)** when performing multiple hypothesis tests at once.

In your DCDD research, since you are testing 11 different attributes (Gender, Race, Skin Tone, etc.), you are essentially rolling the "statistical dice" 11 times. Benjamini-Hochberg is the "correction" that ensures you don't report a lucky roll as a scientific discovery.

---

### 1. The Core Problem: The "Multiple Comparisons" Trap

Imagine you have a fair coin. If you flip it once and get heads, that’s normal. But if you gather 100 people and ask them all to flip a coin 5 times, someone is bound to get 5 heads in a row just by pure chance.

In your audit:

- If you test 11 attributes at a $p < 0.05$ level, there is a **~43% chance** that at least one attribute will show a "significant" result even if the model has zero bias.
    
- This is called the **Family-Wise Error Rate**.
    

### 2. How Benjamini-Hochberg Works

Unlike the **Bonferroni correction** (which is extremely strict and often "kills" real results), Benjamini-Hochberg is more balanced. It doesn't try to eliminate _all_ false positives; it tries to keep the _ratio_ of false positives low.

**The Step-by-Step Logic:**

1. **Rank your results:** You take your 11 "Raw P" values and sort them from smallest to largest.
    
2. **Assign a threshold:** For each p-value, you calculate a specific "cutoff" based on its rank ($i$):
    
    $$\text{Threshold} = \left( \frac{i}{m} \right) \times Q$$
    
    _(Where $i$ is rank, $m$ is total tests, and $Q$ is your chosen False Discovery Rate, usually 0.05)._
    
3. **Find the "Highest Pass":** You look for the largest p-value that is still smaller than its calculated threshold. Everything smaller than that p-value is considered a "True Discovery."