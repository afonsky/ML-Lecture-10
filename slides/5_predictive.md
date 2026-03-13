---
layout: center
---
# Making Predictions

---

# Predicting New Data: The Bayesian Way

<v-clicks depth="2">

* **Frequentist prediction**: plug in $\hat\theta$ → predict using $p(\tilde{x} \mid \hat\theta)$
  * Problem: ignores that $\hat\theta$ is uncertain!

* **Bayesian prediction**: average over **all plausible** $\theta$ values

$$p(\tilde{x} \mid \text{data}) = \int p(\tilde{x} \mid \theta) \cdot p(\theta \mid \text{data}) \, d\theta$$

* This gives the **posterior-predictive distribution** — it accounts for parameter uncertainty

* Result: **wider, more honest prediction intervals**
  * Especially important when you have little data

</v-clicks>

---
zoom: 0.9
---

# Posterior-Predictive Checks: Does My Model Make Sense?

<br>

<div class="grid grid-cols-[4fr_3fr] gap-5">
<div>
<v-clicks depth="2">

* Simple idea: if your model is good, data **simulated from it** should look like **real data**

* Recipe:
  1. Draw a parameter $\theta$ from the posterior
  2. Simulate fake data using that $\theta$
  3. Repeat many times
  4. Compare summaries (mean, spread, shape) of fake vs real data

* If they look very different → your model assumptions are wrong!

* This is one of the **most practical tools** in Bayesian analysis

</v-clicks>
</div>
<div>

<br>

<figure>
  <img src="/seminar/image_006_cell_35.png" style="width: 450px !important; display: block; margin: 0 auto;">
  <figcaption style="color:#b3b3b3ff; font-size: 11px; text-align: center;">Example: comparing a fitted Normal model to observed histogram</figcaption>
</figure>
</div>
</div>