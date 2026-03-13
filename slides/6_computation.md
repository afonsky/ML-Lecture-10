---
layout: center
---
# Computing Bayesian Answers

---

# The Problem: Hard Integrals

<v-clicks depth="2">

* Bayesian inference needs **integrals** over the posterior:
  * Posterior mean: $\mathbb{E}[\theta \mid x] = \int \theta \cdot p(\theta \mid x) \, d\theta$
  * Predictions: $p(\tilde{x} \mid x) = \int p(\tilde{x} \mid \theta) \cdot p(\theta \mid x) \, d\theta$

* For conjugate models (Beta-Binomial, Normal-Normal) → we get exact answers

* For complex models → these integrals are **impossible to compute analytically**

* Two solutions:
  * **Sample** from the posterior (Monte Carlo)
  * **Approximate** the posterior with something simpler (Laplace)

</v-clicks>

---
zoom: 0.9
---

# Monte Carlo: Replace Integrals with Averages

<v-clicks depth="2">

* **Key idea**: draw $S$ random samples $\theta^{(1)}, \ldots, \theta^{(S)}$ from the posterior, then:

$$\mathbb{E}[\theta \mid x] \approx \frac{1}{S} \sum_{s=1}^{S} \theta^{(s)}$$

* More samples → better approximation (by Law of Large Numbers)

* Once you have samples, everything is easy:
  * **Posterior mean** → average of samples
  * **Credible interval** → sort samples, take quantiles
  * **Predictions** → for each $\theta^{(s)}$, simulate new data point

* The challenge is **getting the samples** from complex posteriors
  * MCMC (Markov Chain Monte Carlo) is the standard tool
  * Software: **Stan**, **PyMC**, **NumPyro**

</v-clicks>

---
zoom: 0.9
---

# Laplace Approximation: Quick & Dirty

<div class="grid grid-cols-[4fr_3fr] gap-5">
<div>
<v-clicks depth="2">

* **Idea**: approximate the posterior with a **Gaussian** centered at its peak (MAP estimate)

$$p(\theta \mid x) \approx \mathcal{N}\big(\hat\theta_{\text{MAP}},~ H^{-1}\big)$$

* Steps:
  1. Find the posterior mode $\hat\theta_{\text{MAP}}$ (just optimization!)
  2. Measure the curvature at the peak → gives the spread

* **When it works well**: large datasets, symmetric posteriors
* **When it fails**: small data, skewed or multimodal posteriors

</v-clicks>
</div>
<div>
<figure>
  <img src="/seminar/image_004_cell_27.png" style="width: 450px !important; display: block; margin: 0 auto;">
  <figcaption style="color:#b3b3b3ff; font-size: 11px; text-align: center;">Uncertainty from bootstrap resampling — conceptually similar to MC sampling</figcaption>
</figure>
</div>
</div>

---

# Summary

| Topic | Key Takeaway |
|-------|-------------|
| **Bayes' Rule** | Posterior ∝ Prior × Likelihood |
| **Priors** | Encode prior knowledge; flat prior → MLE |
| **Conjugates** | Same-family prior & posterior; exact updates |
| **Estimators** | Mean, Median, MAP; MAP = regularized MLE |
| **Credible Intervals** | Direct probability for $\theta$; easier than CIs |
| **Predictions** | Average over all $\theta$, not just $\hat\theta$ |
| **Monte Carlo** | Sample from posterior; compute anything |
| **Laplace** | Gaussian approximation; fast but limited |
