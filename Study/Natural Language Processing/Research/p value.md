#### The Null Hypothesis — The "Nothing Is Happening" Assumption

Every statistical test starts with what is called the **null hypothesis**. It is the boring, default assumption that nothing interesting is going on.

In your study the null hypothesis is:

> _"Disability conditioning has no effect on how the model portrays the person. Any differences between neutral and conditioned images are just random noise from the generation process."_

The p-value tells you how likely your results are **assuming this null hypothesis is true**.

- **Small p-value** → your results would be very unlikely if nothing was happening → you have evidence something IS happening
- **Large p-value** → your results are easily explained by chance even if nothing is happening → you cannot conclude anything

---

#### The 0.05 Threshold — Where Does It Come From?

By convention, researchers use **p < 0.05** as the cutoff for calling something significant. This means: _"I am willing to accept a 5% chance of being wrong."_

In other words — if you ran this exact experiment 100 times on data where disability truly had zero effect, you would get p < 0.05 purely by chance about 5 times. You accept that 5% error rate as the price of doing science.

Why 5%? Honestly, it is arbitrary — a convention established decades ago. But it is the universally accepted standard in your field so you follow it.

```
p < 0.05  →  "Significant" — unlikely to be random chance
p ≥ 0.05  →  "Not significant" — could easily be random chance
```

---

#### Now In Your DCDD Study Specifically

For `physical_framing` your test returned **p = 0.0000** (essentially zero).

What this means in plain English:

> _"If disability conditioning truly had no effect on physical framing, the probability of observing a shift this large — Expansive/Commanding dropping from 30% to 11.4% — purely by random chance is essentially zero."_

So you conclude: this shift is real. The disability token is genuinely causing the model to reduce commanding posture. It is not noise.

For `sentiment` your test returned **p = 0.637**.

What this means:

> _"If disability conditioning truly had no effect on sentiment, you would see a distribution difference this large about 63.7% of the time just by chance."_

So you conclude: you cannot claim this is a real effect. 63.7% of the time this would happen even if nothing was going on. It is just noise.