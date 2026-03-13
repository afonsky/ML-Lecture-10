---
layout: center
---
# Conjugate Models & Estimators

---

# Conjugate Families: Why They Matter

<v-clicks depth="2">

* A prior is **conjugate** to a likelihood if the posterior has the **same form** as the prior
  * You put in a Beta → you get out a Beta
  * You put in a Normal → you get out a Normal

* Why do we care? → We can write down the posterior **exactly** — no computation needed!

| Likelihood | Conjugate Prior | Posterior | Example |
|---|---|---|---|
| Binomial | Beta(α, β) | Beta(α+x, β+n−x) | Coin flips |
| Poisson | Gamma(α, β) | Gamma(α+Σy, β+n) | Count data |
| Normal (known σ²) | Normal(μ₀, τ₀²) | Normal(μₙ, τₙ²) | Measurements |

* Prior parameters act as **"pseudo-observations"** — they encode your prior experience

</v-clicks>

---

# Normal-Normal: Intuition

<v-clicks depth="2">

* Observe $x_1, \ldots, x_n \sim \mathcal{N}(\theta, \sigma^2)$, where $\sigma^2$ is known. Prior: $\theta \sim \mathcal{N}(\mu_0, \tau_0^2)$

* **Posterior mean** = weighted average of prior and data:

$$\hat\theta_{\text{Bayes}} = \underbrace{w}_{\text{data weight}} \cdot \bar{x} + \underbrace{(1-w)}_{\text{prior weight}} \cdot \mu_0$$

* Weight $w$ depends on how much data vs how strong the prior:
  * **Lots of data** or **weak prior** → $w \approx 1$ → posterior ≈ MLE
  * **Little data** or **strong prior** → $w \approx 0$ → posterior ≈ prior

* This is **shrinkage** — the same idea as Ridge regression!
  * Ridge penalty $\lambda$ corresponds to prior precision $1/\tau_0^2$

</v-clicks>

---

# Bayes Estimators: Summarizing the Posterior

<v-clicks depth="2">

* The posterior is a full distribution, but sometimes we need a **single number**

| Estimator | What it is | When to use |
|---|---|---|
| **Posterior Mean** | $\mathbb{E}[\theta \mid x]$ | Default choice; best under squared error |
| **Posterior Median** | Middle value | Robust to skewed posteriors |
| **MAP** | Mode of posterior | When you want the most likely value |

* **MAP connects to what you already know**:
  * MAP = maximize $\ln(\text{likelihood}) + \ln(\text{prior})$
  * Gaussian prior → Ridge regression
  * Laplace prior → Lasso regression
  * So regularization = Bayesian estimation with a specific prior!

</v-clicks>

---

# Fun Example: Physicist's Twins

<v-clicks depth="2">

* A physicist learns via sonogram she'll have **twin boys**. What is $\Pr[\text{Identical} \mid \text{Same Sex}]$?

* **Prior** (from medical stats): $\Pr[\text{Identical}] = 1/3$

* **Likelihood**: identical twins are *always* same-sex; fraternal twins have $1/2$ chance

* **Posterior**:

$$\frac{\Pr[\text{Identical} \mid \text{Same}]}{\Pr[\text{Fraternal} \mid \text{Same}]} = \frac{1/3}{2/3} \cdot \frac{1}{1/2} = 1$$

* Answer: $\Pr[\text{Identical} \mid \text{Same}] = 1/2$

* Prior said 2:1 against, but likelihood 2:1 in favor → they **exactly cancel**

</v-clicks>
