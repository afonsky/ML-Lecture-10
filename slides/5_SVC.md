---
zoom: 0.95
--- 

# Support Vector Classifier (SVC)
<br>
<div class="grid grid-cols-[2fr_3fr]">

* MMC problems:
	* Does not exist if classes are not separable (with hyperplane)
	* Highly sensitive to support vectors, i.e. overfits to training observations

<div>
<figure>
	<img src="/ISLRv2_figure_9.6.png" style="width: 550px !important">
	<figcaption style="color:#b3b3b3ff; font-size: 11px">Image source:
	  <a href="https://hastie.su.domains/ISLR2/ISLRv2_website.pdf#page=383">ISLP Fig. 9.6</a>
	</figcaption>
</figure>
</div>
</div>
<br>

* SVC (a.k.a. **soft margin classifier**) uses **slack variables** $\epsilon_i$ and **budget constraint** $C$ to control violations (points crossing the margin or even the hyperplane)
* We solve:
$
\underset{\beta_{0:p},\epsilon_{1:p} \geq 0}{\mathrm{argmax}} \big\{ M ~|~ \sum \beta_j^2 = 1, ~~~~~y_i(\beta_0 + \beta_{p \times 1}^{\prime} x_i) \geq M (1 - \epsilon_i), ~~~~~\sum \epsilon_i \leq C \big\}
$

---

# Slack Variables in SVC

<br>

$$
\underset{\beta_{0:p},\epsilon_{1:p} \geq 0}{\mathrm{argmax}} \big\{ M ~|~ \sum \beta_j^2 = 1, ~~~~~y_i(\beta_0 + \beta_{p \times 1}^{\prime} x_i) \geq M (1 - \epsilon_i), ~~~~~\sum \epsilon_i \leq C \big\}
$$

<div class="grid grid-cols-[5fr_3fr] gap-3">
<div>

* $\epsilon_i = 0 \implies x_i$ is on the correct side of **margin**
* $\epsilon_i \gt 0 \implies x_i$ is on the wrong side of **margin**
* $\epsilon_i \gt 1 \implies x_i$ is on the wrong side of **hyperplane**
* $C > 0 \implies$ fewer than $C$ points<br> can **cross the hyperplane**
* $C$ is a budget hyperparameter
* Support vector have $\epsilon_i \gt 0$
</div>
<div>
  <figure>
    <img src="/ESL_figure_12.1_R.png" style="width: 350px; position: relative">
    <figcaption style="color:#b3b3b3ff; font-size: 11px">Image source:
      <a href="https://hastie.su.domains/ElemStatLearn/printings/ESLII_print12.pdf#page=437">ESL Fig. 12.1 (right)</a>
    </figcaption>
  </figure>
</div>
</div>