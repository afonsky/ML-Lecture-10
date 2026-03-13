---
layout: center
---
# Credible Intervals & Model Comparison

---

# Credible Intervals: Bayesian Uncertainty

<div class="grid grid-cols-[1fr_1fr] gap-5">
<div>
<v-clicks depth="2">

* A **credible interval** (CrI) answers: "Where does $\theta$ probably lie?"

* 95% CrI $[a, b]$ means: *"Given the data, there is 95% probability that $\theta \in [a, b]$"*

* Two types:
  * **Equal-tailed**: cut off 2.5% from each tail
  * **HPD** (Highest Posterior Density): shortest interval with 95% mass

* Much simpler to interpret than confidence intervals!

</v-clicks>
</div>
<div>
<figure>
  <img src="/seminar/image_009_cell_54.png" style="width: 440px !important;">
  <figcaption style="color:#b3b3b3ff; font-size: 11px;">Posterior with 95% credible interval (shaded region)</figcaption>
</figure>
</div>
</div>

---

# CrI vs Confidence Interval

<v-clicks depth="2">

* **Confidence interval** (frequentist):
  * "If I repeated the experiment 1000 times, ~950 of my intervals would contain the true $\theta$"
  * Says nothing about *this particular* interval!

* **Credible interval** (Bayesian):
  * "Given the data I observed, there is 95% probability that $\theta$ is in this interval"
  * Direct probability statement — much more intuitive

* With large $n$ and flat priors, they are often numerically similar
  * But the **interpretation** is fundamentally different

</v-clicks>

---

# Model Comparison: Bayes Factors

<v-clicks depth="2">

* How do we compare two models $\mathcal{M}_1$ vs $\mathcal{M}_2$?

* Compute the **Bayes factor**: ratio of how well each model predicts the data

$$BF_{12} = \frac{p(\text{data} \mid \mathcal{M}_1)}{p(\text{data} \mid \mathcal{M}_2)}$$

* Interpretation:

| $BF_{12}$ | Evidence |
|---|---|
| 1 – 3 | Barely worth mentioning |
| 3 – 20 | Positive evidence for $\mathcal{M}_1$ |
| 20 – 150 | Strong evidence |
| > 150 | Very strong evidence |

* Unlike p-values, Bayes factors can **support the null hypothesis** (not just fail to reject)

</v-clicks>
