# Support Vector Machines (SVM)
<br>

* We can further extend SVC by adding non-linear terms  $X_i^d, X_i X_j, ...$
	* However, optimization requires significant computing resources
* Instead, we can use a **kernel trick**
* Consider a **linear kernel** for $u, v \in \R^p$:
$
~K(u, v) = \langle u, v \rangle = \sum\limits_{j=1}^p u_j v_j = u \cdot v = u^{\prime}v
$
* It turns out that SVC optimization can be rewritten via
$
f(x) = \sum\limits_{i=1}^n \alpha_i K(x, x_i)
$
	* To estimate $\alpha_{1:n}$ and $\beta_0$ we need $\frac{n(n-1)}{2}$ **inner products**... , however...
	* $\alpha \neq 0$ only for the support vectors
		* So, estimation simplifies to
$
f(x) = \sum\limits_{i \in S}^n \alpha_i K(x, x_i)
$,

where $S$ is a set of support vectors (determined during training)

---

# Kernels in Machine Learning

* Many linear parametric models can be re-cast into an equivalent ‘dual representation’ in which the predictions are also based on linear combinations of a kernel function evaluated at the training data points
	* For models which are based on a fixed nonlinear feature space mapping $\phi(x)$, the kernel function is given by the relation<br> $k(\bm{x, x}^\prime) = \phi(\bm{x})^T \phi(\bm{x}^\prime)$
		* The kernel is a symmetric function of its arguments:<br> $k(\bm{x, x}^\prime) = k(\bm{x}^\prime, \bm{x})$
	* The simplest example of a kernel function is **linear kernel**:<br> $\phi(x) = x$, in which case $k(\bm{x, x}^\prime) = \bm{x}^T \bm{x}^\prime$

---
zoom: 0.95
--- 

# SVM Kernels

* The nonlinear classifier works by considering a nonlinear transformation $\phi(x)$ from the original space into a higher dimensional space
	* This nonlinear transformation can increase the linear separability of the classes
	* In practice, all dot products are replaced by the $K(x, x_i)$ kernel

<br>
<figure>
	<img src="/kernel.png" style="width: 580px !important">
	<figcaption style="color:#b3b3b3ff; font-size: 11px">Image source:
	  <a href="https://ipython-books.github.io/85-using-support-vector-machines-for-classification-tasks/">https://ipython-books.github.io/85-using-support-vector-machines-for-classification-tasks/</a>
	</figcaption>
</figure>

---

# We can also add non-linearity via
<br>

* **Polynomial kernel** of degree $d$:
$$
K(u,v) = (1 + \sum\limits_{j=1}^p u_j v_j)^d
$$

* **Radial (basis) kernel** of degree $d$:
$$
K(u,v) = \mathrm{exp}\Big[-\gamma \sum\limits_{j=1}^p (u_j - v_j)^2 \Big] = \mathrm{exp}\Big[-\gamma ||u_j - v_j||_2^2 \Big] ~~~\mathrm{\textcolor{black}{for}} ~~~\gamma \gt 0
$$

* **Neural network kernel**:
$$
K(u,v) = \mathrm{tanh}\Big[a \langle u, v \rangle + r \Big]
$$

---

# Radial Basis Kernel, $\mathrm{exp}\big[-\gamma ||u_j - v_j||_2^2 \big]$

<div class="grid grid-cols-[4fr,3fr]">
<div>

* It is essentially an unscaled Gaussian PDF
* Large $u - v$ implies near zero exponent
* So, in $f(x) = \beta_0 + \sum\limits_{i \in S}^n \alpha_i K(x, x_i)$
	* $\alpha = 0$ for non-support vectors, or
	* $K(x, x_i) \approx 0$ for distant observations $x_i$

</div>
<div>
<figure>
	<img src="/Normal_Distribution_PDF.svg" style="width: 250px !important">
	<figcaption style="color:#b3b3b3ff; font-size: 11px">Image source:
	  <a href="https://en.wikipedia.org/wiki/Normal_distribution">https://en.wikipedia.org/wiki/Normal_distribution</a>
	</figcaption>
</figure>
</div>
</div>

* Hence, only neighboring support vectors participate in forming a decision boundary
<div class="grid grid-cols-[3fr,3fr]">
<div>
	<br>
</div>
<div>
<figure>
	<img src="/ISLRv2_figure_9.9.png" style="width: 330px !important">
	<figcaption style="color:#b3b3b3ff; font-size: 11px">Image source:
	  <a href="https://hastie.su.domains/ISLR2/ISLRv2_website.pdf#page=390">ISLR Fig. 9.9</a>
	</figcaption>
</figure>
</div>
</div>

---

# Ex. SVM vs LDA on Heart Disease Data
<br>

* Both SVM & LDA compute scores of the form<br>
$\hat{f}(X) = \hat{\beta}_0 + \hat{\beta}_1 X_1 + \hat{\beta}_2 X_2 + ... + \hat{\beta}_p X_p$
<br>


<figure>
	<br>
	<br>
	<img src="/ISLP_figure_9.11.png" style="width: 520px !important">
	<figcaption style="color:#b3b3b3ff; font-size: 11px">Image source:
	  <a href="https://hastie.su.domains/ISLR2/ISLRv2_website.pdf#page=392">ISLP Fig. 9.11</a>
	</figcaption>
</figure>

---

# SVM is a Binary Classifier

* ... but can be extended to multiclass.
* Consider $K > 2$ classes and a test observation $x^{*}$
* **One-versus-one** (OVO) approach
	* Fit $\binom{K}{2}$ pairwise SVMs 
	* Assign $x^{*}$ to the most frequently predicted class
	* Disadvantage: lots of models to fit and inference with
* **One-versus-all** (OVA) approach
	* Fit $K$ SVMs for one of $K$ classes versus all other $K - 1$ classes combined
	* Assign $x^{*}$ to the class with greatest $\beta_{0k} + \beta_{1k}^{\prime} x_1^{*} + ... + \beta_{pk}^{\prime} x_p^{*}$ value
		* Where $\beta_{ik}$ are fitted for each class $k = 1:K$
	* Disadvantage: even if we start with **balanced** $K$ classes, we will face **imbalanced** aggregated classes, which will require probability threshold tuning

---

# SVM vs Logistic Regression
<br>

* Another form for SVM is
$
~~\underset{\beta_{0:p}}{\mathrm{argmin}} \bigg\{ \sum\limits_{i=1}^n \underbrace{\mathrm{max}[0, 1 - y_i f(x_i)]}_{\text{\textcolor{grey}{Hinge loss}}} ~+ \underbrace{\lambda \sum\limits_{j=1}^p \beta_j^2}_{\text{\textcolor{grey}{Ridge penalty}}} \bigg\},
$
<br>

<div class="grid grid-cols-[4fr_3fr]">
<div>

where $\lambda \geq 0$ and correlates with the parameter $C$

* Hinge loss is similar to logistic regression loss
* Changing the loss function yields a regularized logistic regression
</div>
<div>
<figure>
	<br>
	<img src="/ISLRv2_figure_9.12.png" style="width: 280px !important">
	<figcaption style="color:#b3b3b3ff; font-size: 11px">Image source:
	  <a href="https://hastie.su.domains/ISLR2/ISLRv2_website.pdf#page=395">ISLR Fig. 9.12</a>
	</figcaption>
</figure>
</div>
</div>

---
layout: iframe

# SVM Playground
url: http://macheads101.com/demos/svm-playground/
---
