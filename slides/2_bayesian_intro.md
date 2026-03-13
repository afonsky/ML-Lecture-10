---
layout: center
---
# Bayesian Inference


---

# Bayes' Theorem — The Core Formula

<div class="grid grid-cols-[3fr_1fr] gap-5">
<div>
<v-clicks depth="2">

* Thomas Bayes (1702–1761) gave us this simple rule:

$$
\color{grey}\underbrace{\color{#006} f(\theta | x)}_{\mathrm{posterior}} \color{red} \propto
\color{grey}\underbrace{\color{#006} f(\theta)}_{\mathrm{prior}} \color{#006} \cdot
\color{grey}\underbrace{\color{#006} f(x | \theta)}_{\mathrm{likelihood}}
$$

* **Prior** $f(\theta)$ — what we believe about $\theta$ *before* seeing data
* **Likelihood** $f(x|\theta)$ — how likely the data is under each $\theta$
* **Posterior** $f(\theta|x)$ — updated belief *after* seeing data

* That's it! **Multiply** the prior by the likelihood, **normalize**, done

</v-clicks>
</div>
<div>
<figure>
  <img src="/Thomas_Bayes.gif" style="width: 135px !important">
  <figcaption style="color:#b3b3b3ff; font-size: 11px">Thomas Bayes<br>(1702—1761)
  </figcaption>
</figure>
</div>
</div>

---

# How It Works: Prior × Likelihood → Posterior

<div class="grid grid-cols-[1fr_1fr] gap-5">
<div>
<v-clicks depth="2">

* **Start** with a prior (your initial guess)
* **Observe** data and compute likelihood
* **Multiply** them together (pointwise)
* **Normalize** to get the posterior

* As you collect more data, the **likelihood dominates** and the prior matters less

* With enough data, Bayesian and frequentist answers **agree**!

</v-clicks>
</div>
<div>
<figure>
  <img src="/prior2post_1-1.svg" style="width: 440px !important">
  <figcaption style="color:#b3b3b3ff; font-size: 11px">Prior × Likelihood = Posterior. Source:
    <a href="https://m-clark.github.io/bayesian-basics/example.html">m-clark.github.io</a>
  </figcaption>
</figure>
</div>
</div>

---

# Intuitive Example: Spelling Correction

<v-clicks depth="2">

* A text contains the word "$\mathrm{radom}$". Should it be "$\mathrm{random}$", "$\mathrm{radon}$", or really "$\mathrm{radom}$"?

| Intended word ($\theta$) | Prior (word frequency) | Likelihood (typo prob.) | Posterior ∝ |
|---|---|---|---|
| random | $8 \times 10^{-5}$ (common) | 0.00193 (easy typo) | $\mathbf{1.5 \times 10^{-7}}$ ✅ |
| radon | $6 \times 10^{-6}$ (rare) | 0.000143 (harder typo) | $8.6 \times 10^{-10}$ |
| radom | $3 \times 10^{-7}$ (very rare) | 0.975 (typed correctly) | $2.9 \times 10^{-7}$ |

* The **posterior** picks $\theta = \text{random}$ — combining word frequency *and* typo probability
* Neither prior nor likelihood alone would give the right answer!

</v-clicks>

---
zoom: 0.95
---

# Choosing a Prior

<div class="grid grid-cols-[4fr_3fr] gap-5">
<div>
<v-clicks depth="2">

* **Informative prior** — you have real prior knowledge
  * "Body temperature is around 37°C"<br> → $\theta \sim \mathcal{N}(37, 0.5^2)$
  
* **Weakly informative prior** — reasonable range, not too specific
  * "This proportion is between 0 and 1, probably not extreme" → $\theta \sim \mathrm{Beta}(2, 2)$
  
* **Flat (uninformative) prior** — no opinion at all
  * "Any value is equally likely" → $\theta \sim \mathrm{Uniform}$
  * With a flat prior, the posterior ≈ likelihood<br> → you get **MLE**!
</v-clicks>
</div>
<div>
<br>
<br>
<br>
<v-click>
<figure>
  <img src="/uniform_prior.png" style="width: 400px !important; display: block; margin: 0 auto;">
  <figcaption style="color:#b3b3b3ff; font-size: 11px; text-align: center;">Uniform (flat) prior — every value is equally likely</figcaption>
</figure>
</v-click>
</div>
</div>

---
zoom: 0.77
---

# How Priors Affect the Posterior

<div class="grid grid-cols-[1fr_1fr] gap-5">
<div>

<br>
<br>
<br>
<v-clicks depth="2">

* **Stronger prior** = more concentrated → pulls the posterior toward the prior mean

* **Weaker prior** = more spread out → data dominates

* With **enough data**, all reasonable priors give similar posteriors

* Rule of thumb: the prior acts like "extra observations"

</v-clicks>

<br>
<br>
<br>

<div style="color:#b3b3b3ff; font-size: 11px;">Images: Prior sensitivity: changing the strength κ of the prior.<br>Strong priors (κ=200) dominate; weak priors let data speak.</div>
</div>
<div>
<figure>
  <img src="/seminar/image_010_cell_60.png" style="width: 460px !important;">
</figure>
</div>
</div>

---

# Running Example: Coin Flips (Beta-Binomial)

<v-clicks depth="2">

* **Data**: flip a coin $n$ times, observe $x$ heads
  * Likelihood: $\mathrm{Binomial}(x \mid n, \theta)$ — where $\theta$ = probability of heads

* **Prior**: $\theta \sim \mathrm{Beta}(\alpha, \beta)$ — flexible distribution on $[0, 1]$

</v-clicks>

<div class="grid grid-cols-[1fr_1fr] gap-25">
<div>
<v-clicks depth="2">

* **Posterior**: also a Beta distribution!
$$\theta \mid x \sim \mathrm{Beta}(\alpha + x,~ \beta + n - x)$$

* This is called a **conjugate** family: <br>prior and posterior have the same form

* Think of $\alpha$ as **"prior heads"** and $\beta$ as **"prior tails"**

</v-clicks>
</div>
<div>
<figure>
  <img src="/binomial_PMF.png" style="width: 270px !important;">
  <figcaption style="color:#b3b3b3ff; font-size: 11px;">More data → narrower posterior (more certainty)</figcaption>
</figure>
</div>
</div>

---

# What Does Beta Look Like?

<div class="grid grid-cols-[1fr_1fr] gap-5">
<div>
<v-clicks depth="2">

* $\mathrm{Beta}(\alpha, \beta)$ is a flexible distribution on $[0,1]$
* Controls shape of our belief about $\theta$:
  * $\mathrm{Beta}(1, 1)$ = Uniform (no preference)
  * $\mathrm{Beta}(2, 5)$ = "θ is probably small"
  * $\mathrm{Beta}(50, 50)$ = "θ is near 0.5"

* After observing data, the posterior is:<br>$\mathrm{Beta}(\alpha + x,~ \beta + n - x)$

</v-clicks>
</div>
<div>
<figure>
  <img src="/seminar/image_011_cell_64.png" style="width: 440px !important;">
  <figcaption style="color:#b3b3b3ff; font-size: 11px;">Example: Beta(2, 5) distribution — belief that θ is likely small</figcaption>
</figure>
</div>
</div>

---
zoom: 0.95
---

# Default Priors: Uniform vs Jeffreys'

<div class="grid grid-cols-[1fr_1fr] gap-5">
<div>
<v-clicks depth="2">

* When you have no prior knowledge, two common choices:

* **Uniform** $\mathrm{Beta}(1, 1)$:
  * All values equally likely
  * Simple but can be misleading

* **Jeffreys'** $\mathrm{Beta}(\tfrac{1}{2}, \tfrac{1}{2})$:
  * Gives extra weight near 0 and 1
  * Mathematically "objective" — doesn't change if you reparameterize

* Both are **non-informative**: they let the data speak

</v-clicks>
</div>
<div>
<figure>
  <img src="/seminar/image_012_cell_66.png" style="width: 440px !important;">
  <figcaption style="color:#b3b3b3ff; font-size: 11px;">Uniform Beta(1,1) vs Jeffreys' Beta(½, ½) priors</figcaption>
</figure>
</div>
</div>

---

# Real Example: Placenta Previa

<div class="grid grid-cols-[1fr_1fr] gap-5">
<div>
<v-clicks depth="2">

* **Question**: Is the proportion of female births different for placenta previa pregnancies?

* **Data**: 437 girls out of 980 births
* **Prior**: $\mathrm{Beta}(1, 1)$ (uniform — no prior opinion)
* **Posterior**: $\mathrm{Beta}(438, 544)$

* Posterior mean: $\frac{438}{982} = 0.446$
  * Compare to general rate: $0.485$
  * The posterior says "probably slightly lower"

* The 95% **credible interval** shows the range of plausible values

</v-clicks>
</div>
<div>
<figure>
  <img src="/seminar/image_009_cell_54.png" style="width: 440px !important;">
  <figcaption style="color:#b3b3b3ff; font-size: 11px;">Posterior Beta(438, 544) with 95% credible interval</figcaption>
</figure>
</div>
</div>

---
zoom: 0.9
---

# Literature and Links

* This week's topic is covered in [CASI](https://hastie.su.domains/CASI_files/PDF/casi.pdf) (Chapter 3) and [BDA3](https://users.aalto.fi/~ave/BDA3.pdf) (Chapters 1–4)

<div class="grid grid-cols-[1fr_1fr] gap-5">
<div>
<figure>
  <img src="/CASI_cover.jpg" style="width: 200px !important;">
</figure>
</div>
<div>
<figure>
  <img src="/BDA_cover.jpeg" style="width: 210px !important;">
</figure>
</div>
</div>
<br>

* [Prior choice recommendations (Stan wiki)](https://github.com/stan-dev/stan/wiki/Prior-Choice-Recommendations)
* [Bayesian Data Analysis course (Aalto University)](https://avehtari.github.io/BDA_course_Aalto/)
