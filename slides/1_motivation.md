---
layout: center
---
# Why Bayesian Inference?

---

# The Story So Far: Fitting Models

<br>

<div class="grid grid-cols-[4fr_3fr] gap-5">
<div>
<v-clicks depth="2">

* All semester you've been doing **frequentist ML**:
  * Pick a model<br>↓<br> fit parameters<br>↓<br> evaluate on test data

* Example: **Linear regression** on kidney data<br> — we get one best-fit line + a confidence band

</v-clicks>
</div>
<div>
<v-click>
<figure>
  <img src="/seminar/image_001_cell_13.png" style="width: 550px !important; display: block; margin: 0 auto;">
  <figcaption style="color:#b3b3b3ff; font-size: 11px; text-align: center;">OLS fit with 95% mean CI and prediction band (kidney data from CASI)</figcaption>
</figure>
</v-click>
</div>
</div>

---

# The Problem: One Best Guess

<v-clicks depth="2">

* **MLE** gives us a single **point estimate** $\hat\theta$ — one "best" number
  * But how confident should we be in it?
  * We use bootstrap, SE, confidence intervals... all **indirect**

* What if we could get a **full picture** of all plausible parameter values?

* **Regularization** you already know is secretly Bayesian!
  * Ridge penalty $\lambda\|\theta\|^2$ = assuming $\theta$ is probably near zero (Gaussian prior)
  * Lasso penalty $\lambda\|\theta\|_1$ = assuming $\theta$ is probably exactly zero (Laplace prior)

</v-clicks>

---

# The Bayesian Idea

<v-clicks depth="2">

* Instead of a single $\hat\theta$, compute the **distribution of plausible values** of $\theta$ given data

* This naturally gives us:
  * **Best guess** — e.g. posterior mean
  * **How sure we are** — credible intervals
  * **Predictions with uncertainty** — not just one prediction, but a range

* Especially useful when:
  * **Little data** — prior knowledge helps (think: rare diseases, small experiments)
  * **Uncertainty matters** — medical decisions, self-driving cars
  * **Sequential learning** — today's answer becomes tomorrow's starting point
</v-clicks>

---

# Frequentist vs Bayesian: Key Differences

| | Frequentist | Bayesian |
|---|---|---|
| Parameter $\theta$ | Fixed unknown number | Has a probability distribution |
| Data | Random (imaginary repeats) | Fixed (what we observed) |
| Result | Point estimate $\hat\theta$ | Full posterior distribution $p(\theta \mid x)$ |
| Uncertainty | Confidence intervals | Credible intervals |

<br>

<v-click>

> Think of it this way:<br> **Frequentist** asks "What would happen if I repeated the experiment 1000 times?"<br> **Bayesian** asks "Given what I saw, what do I believe now?"
</v-click>