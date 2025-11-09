# Hyperplane in 1D

<div class="grid grid-cols-[1fr_1fr]">
<div>
<v-plotly style="width: 400px !important; height: 200px !important"
:data="[{
x: Array.from({length: 15}, () => Math.random()*4.5),
y: Array.from({length: 15}, () => Math.random()*0),
type: 'scatter',
mode: 'markers',
marker: {color: 'red', size: 10, opacity: 0.5},
showlegend: false
},
{
x: Array.from({length: 15}, () => Math.random()*4.5+5.5),
y: Array.from({length: 15}, () => Math.random()*0),
type: 'scatter',
mode: 'markers',
marker: {color: 'green', size: 10, opacity: 0.5},
showlegend: false
},
{
x: [5.0],
y: [0],
type: 'scatter',
mode: 'markers',
marker: {color: 'blue', size: 10, symbol: 'cross'},
showlegend: false
}]"
:layout="{
xaxis: {zeroline: false},
yaxis: {showticklabels: false, showgrid: false},
margin: {l: 10, r:50, pad: 1}
}"
:config="{displayModeBar: false}"
:options="{}"/>
</div>
<div>
<div v-click>
<v-plotly style="width: 530px !important; height: 200px !important"
:data="[{
x: Array.from({length: 15}, () => Math.random()*3),
y: Array.from({length: 15}, () => Math.random()*0),
type: 'scatter',
mode: 'markers',
marker: {color: 'red', size: 10, opacity: 0.5},
showlegend: false
},
{
x: Array.from({length: 15}, () => Math.random()*3+3.5),
y: Array.from({length: 15}, () => Math.random()*0),
type: 'scatter',
mode: 'markers',
marker: {color: 'green', size: 10, opacity: 0.5},
showlegend: false
},
{
x: Array.from({length: 15}, () => Math.random()*3+7),
y: Array.from({length: 15}, () => Math.random()*0),
type: 'scatter',
mode: 'markers',
marker: {color: 'red', size: 10, opacity: 0.5},
showlegend: false
}]"
:layout="{
title: 'Separating hyperplane does not always exist',
xaxis: {zeroline: false},
yaxis: {showticklabels: false, showgrid: false},
margin: {l: 50, r:30, pad: 1}
}"
:config="{displayModeBar: false}"
:options="{}"/>
</div>
</div>
</div>

* It's a point in 1D space for $\beta_i \in \R$,
$$
P := \{x ~|~\beta_0 + \beta_1 x = 0\} = \biggl\{ x ~| \begin{bmatrix}
   \beta_0 \\
   \beta_1
\end{bmatrix} \perp \begin{bmatrix}
   1 \\
   x
\end{bmatrix} \biggr\} = \{-\beta_0/\beta_1\}
$$

* A single point satisfies the set’s condition

<!--
* Poly. Reg is in fact the change of the representation of the predictor's space
* PCR is composed from constant segments
-->

---
zoom: 0.96
--- 

# Hyperplane in 2D

* It’s a line in 2D space,
$L := \{x ~|~\beta_0 + \beta_1 x_1 + \beta_2 x_2 = 0\} \subset \R^2$
<div class="grid grid-cols-[4fr_2fr]">
<div>
<br>

   * This is almost equivalent to a common line equation: $x_2 = -\frac{\beta_0}{\beta_2} -\frac{\beta_1}{\beta_2}x = b_0 + b_1 x$
<br>

      * The set definition allows $\beta_2 = 0$, which is a vertical line
        * The functional definition does not allow vertical lines (or 2 distinct outputs at any $x_1$)
        * The set’s condition states that coefficient vector is orthogonal to the $\begin{bmatrix}
   1 \\
   x
\end{bmatrix}$
</div>
<div>
<v-plotly style="width: 400px !important; height: 400px !important"
:data="[{
x: Array.from({length: 25}, () => Math.random()*0.45),
y: Array.from({length: 25}, () => Math.random()*0.45),
type: 'scatter',
mode: 'markers',
marker: {color: 'red', size: 10, opacity: 0.5},
showlegend: false
},
{
x: Array.from({length: 15}, () => Math.random()*0.55+0.5),
y: Array.from({length: 15}, () => Math.random()*0.55+0.5),
type: 'scatter',
mode: 'markers',
marker: {color: 'green', size: 10, opacity: 0.5},
showlegend: false
},
{
x: [0, 0.9],
y: [1.05, 0],
type: 'scatter',
mode: 'lines',
line: {color: 'blue'},
showlegend: false
}]"
:layout="{
xaxis: {title: 'x<sub>1</sub>'},
yaxis: {title: 'x<sub>2</sub>'},
margin: {l: 40, r:20, b:70, t:20, pad: 2}
}"
:config="{displayModeBar: false}"
:options="{}"/>
</div>
</div>

---

# Hyperplane in 3D

* It’s a plane in 3D space,
$
H := \{x ~|~\beta_0 + \beta_1 x_1 + \beta_2 x_2 + \beta_3 x_3 = 0\} \subset \R^3
$
<div>
<v-plotly style="height: 400px; position: relative"
:data="[{
x: Array.from({length: 25}, () => Math.random()*0.5),
y: Array.from({length: 25}, () => Math.random()*0.5),
z: Array.from({length: 25}, () => Math.random()*0.5),
type: 'scatter3d',
mode: 'markers',
marker: {color: 'red', size: 4, opacity: 0.5},
showlegend: false
},
{
x: Array.from({length: 15}, () => Math.random()*0.6+0.5),
y: Array.from({length: 15}, () => Math.random()*0.6+0.5),
z: Array.from({length: 15}, () => Math.random()*0.6+0.5),
type: 'scatter3d',
mode: 'markers',
marker: {color: 'green', size: 4, opacity: 0.5},
showlegend: false
},
{
x: [0,1,1,0],
y: [0.9,0.4,0.2,0.7],
z: [0,0,1.0,1.0],
i: [0,0,0,1],
j: [1,2,3,2],
k: [2,3,1,3],
type: 'mesh3d',
color: 'blue',
opacity: 0.35,
showlegend: false
}]"
:layout="{
   scene: {camera: {eye: {x: 1.75, y: -1.25, z:1.05}},
            xaxis: {title: 'x<sub>1</sub>', range: [0.01,1]},
            yaxis: {title: 'x<sub>2</sub>', range: [0.,1]},
            zaxis: {title: 'x<sub>3</sub>', range: [0.,1]}},
   margin: {l: 20, r:20, b:20, t:1, pad: 5},
}"
:config="{displayModeBar: false}"
:options="{}"/>
</div>

---
zoom: 0.93
---

# Hyperplane in $p$ Dimensions

<div class="grid grid-cols-[3fr_2fr] gap-6">
<div>

* We can’t visualize the hyperplane for $p > 3$ 😳
* It’s a $~p - 1~$ dimensional object<br> in $p$ dimensional space, $\{x_{p \times 1} ~|~\beta_0 + \beta_{p \times 1}^{T} x = 0\}$
</div>
<div>
  <figure>
    <img src="/hyperplane.png" style="width: 240px !important;">
    <figcaption style="color:#b3b3b3ff; font-size: 11px; float: right;">Image source: <a href="https://www.researchgate.net/publication/228734473_Linear_conic_programming">https://www.researchgate.net/publication/228734473_Linear_conic_programming</a>
    </figcaption>
  </figure>
</div>   
</div>

* $p$-dimensional space can be partitioned into:<br>
$
\color{grey}\underbrace{\color{#006}\{x ~|~\beta_0 + \beta^{T} x \lt 0\}}_{\text{\textcolor{grey}{half-plane}}}
\color{#006}\cup
\color{grey}\underbrace{\color{#006}\{x ~|~\beta_0 + \beta^{T} x = 0\}}_{\text{\textcolor{grey}{hyper-plane}}}
\color{#006}\cup
\color{grey}\underbrace{\color{#006}\{x ~|~\beta_0 + \beta^{T} x \gt 0\}}_{\text{\textcolor{grey}{half-plane}}}
$

   * $\beta_0$ makes hyperplane an “**affine set**” (may not pass through **0**)

---

# Linear Algebra of a Hyperplane

* Affine set $L$ (a hyperplane) is defined as $L := \{x_{2 \times 1} ~|~\beta_0 + \beta_1 x_1 + \beta_2 x_2 = 0\}$

<div class="grid grid-cols-[3fr_2fr]">
<div>

* Properties of $L$:
   * $\forall x_1, x_2 \in L$ we have $\beta^{T}(x_1 - x_2) = 0$
      * i.e. $\vec\beta$ is **orthogonal** to $L$
         * So, $\vec{\beta}^{*} := \frac{\vec\beta}{||\vec\beta||}$ is a **normal** vector to $L$

      * $\forall x_0 \in L$, we have $\beta^{T}x_0 = -\beta_0$
      * $\forall x \in \R^p$, the **signed distance** is
<br> $d(L,x) = \beta^{*T} (x - x_0) \propto \beta^{T} (x - x_0)$

</div>
<div>
  <figure>
   <br>
   <br>
    <img src="/Hyperplane_th.png" style="width: 500px">
    <figcaption style="color:#b3b3b3ff; font-size: 11px">Based on
      <a href="https://hastie.su.domains/ElemStatLearn/printings/ESLII_print12.pdf#page=149">ESL Fig. 4.15</a>
    </figcaption>
  </figure>
</div>
</div>

---

# Linear Algebra of a Hyperplane

* Affine set $L$ (a hyperplane) is defined as $L := \{x_{2 \times 1} ~|~\beta_0 + \beta_1 x_1 + \beta_2 x_2 = 0\}$

<div class="grid grid-cols-[3fr_2fr]">
<div>

* Properties of $L$:
   * $\forall x_1, x_2 \in L$ we have $\beta^{T}(x_1 - x_2) = 0$
      * i.e. $\vec\beta$ is **orthogonal** to $L$
         * So, $\vec{\beta}^{*} := \frac{\vec\beta}{||\vec\beta||}$ is a **normal** vector to $L$

      * $\forall x_0 \in L$, we have $\beta^{T}x_0 = -\beta_0$
      * $\forall x \in \R^p$, the **signed distance** is
<br> $d(L,x) = \beta^{*T} (x - x_0) \propto \beta^{T} (x - x_0)$

</div>
<div>
  <figure>
   <br>
   <br>
    <img src="/Hyperplane_ex.png" style="width: 500px">
    <figcaption style="color:#b3b3b3ff; font-size: 11px">Based on
      <a href="https://hastie.su.domains/ElemStatLearn/printings/ESLII_print12.pdf#page=149">ESL Fig. 4.15</a>
    </figcaption>
  </figure>
</div>
</div>

---

# Separating Hyperplanes

* We want to find a **separating hyperplane** (if possible), which perfectly separates the observations of two classes, $y = \pm 1$

$$
\color{grey}\underbrace{\color{#006}\{x ~|~\beta_0 + \beta^{T} x \lt 0\}}_{\text{\textcolor{grey}{y = -1}}}
\color{#006}\cup
\color{grey}\underbrace{\color{#006}\{x ~|~\beta_0 + \beta^{T} x = 0\}}_{\text{\textcolor{grey}{hyper-plane}}}
\color{#006}\cup
\color{grey}\underbrace{\color{#006}\{x ~|~\beta_0 + \beta^{T} x \gt 0\}}_{\text{\textcolor{grey}{y = 1}}}
$$

* **Training**: estimate $\beta_i$ parameters as $\hat{\beta}_i$
* **Inference**: classify new $x^{*}$ as $\mathrm{sign}(\beta_0 + \beta^{T} x^{*})$ 
   * Distance of $x_{p \times 1}^{*}$ to the hyperplane, $|\beta_0 + \beta^{T}x^{*}|$, indicates confidence of prediction
