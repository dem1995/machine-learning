---
layout: default
title: Linear Algebra
parent: Curriculum
nav_order: 1.5
---


### External Resources
- [Brian Sanderson (3Blue1Brown)'s _Essence of Linear Algebra_ series](https://www.youtube.com/watch?v=fNk_zzaMoSs&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab&ab_channel=3Blue1Brown) provides a _fantastic_ introduction to linear algebra (and the 15-part series, in totality, covers what a first-year course in the subject would). For this course, remembering the videos' contents is possibly overkill, but you may find that having at least an awareness of their material proves useful. Episodes 1-9 provide a fairly comprehensive overview of linear transformations and dot products.

- ["Foundations of Machine Learning: Linear Algebra"](https://the-learning-machine.com/article/machine-learning/linear-algebra) is your referential pal whenever you need to know more about a linear algebraic terms for this course (as well as for material beyond the scope of this course). It lays out terms and descriptions of them in friendly, easily-digestible chunks, and offers interactive visualizations of a number of them for your convenience.

# Linear Algebra
## Overview
At its core, linear algebra is about two things: representation and transformation. In the context of this course, data is represented as _vectors_ and usually processed by _matrices_. When you multiply a matrix _**M**_ by a column vector **v** (i.e. **_M_**__v__), the rows of the matrix are each multiplied by the vector in an elementwise faction. More explicitly,

<img src="https://i.upmath.me/svg/%5Cboldsymbol%7B%5Cmathit%7BM%7D%7D%5Cvec%7Bv%7D%20%3D%20%0A%5Cbegin%7Bbmatrix%7D%0Am_%7B11%7D%20%26%20m_%7B12%7D%20%5C%5C%0Am_%7B21%7D%20%26%20m_%7B22%7D%20%5C%5C%0Am_%7B31%7D%20%26%20m_%7B32%7D%0A%5Cend%7Bbmatrix%7D%0A%5Cbegin%7Bbmatrix%7D%0Av_%7Ba%7D%20%5C%5C%0Av_%7Bb%7D%20%0A%5Cend%7Bbmatrix%7D%3D%0A%5Cbegin%7Bbmatrix%7D%0Am_%7B11%7D%20%5Ccdot%20v_a%20%2B%20m_%7B12%7D%20%5Ccdot%20v_b%5C%5C%0Am_%7B21%7D%20%5Ccdot%20v_a%20%2B%20m_%7B22%7D%20%5Ccdot%20v_b%5C%5C%0Am_%7B31%7D%20%5Ccdot%20v_a%20%2B%20m_%7B32%7D%20%5Ccdot%20v_b%0A%5Cend%7Bbmatrix%7D%0A" alt="\boldsymbol{\mathit{M}}\vec{v} = 
\begin{bmatrix}
m_{11} &amp; m_{12} \\
m_{21} &amp; m_{22} \\
m_{31} &amp; m_{32}
\end{bmatrix}
\begin{bmatrix}
v_{a} \\
v_{b} 
\end{bmatrix}=
\begin{bmatrix}
m_{11} \cdot v_a + m_{12} \cdot v_b\\
m_{21} \cdot v_a + m_{22} \cdot v_b\\
m_{31} \cdot v_a + m_{32} \cdot v_b
\end{bmatrix}
" />

or, as a further visual,

![Matrix-vector multiplication visual](matmul.png)

### Motivating Example

Now, suppose we're dealing with chocolate-chip cookies, and we want to encode information about the chocolate chips and cookie dough used. We might care about the volume, that is, how many Commonwealth cups\* of each we have. Suppose in our last batch of cookies we used 10 cups of dough and 2 cups of chocolate-chip cookies. We might represent this, then, as

<img src="https://i.upmath.me/svg/%5Cvec%7Bv%7D%3D%5Cbegin%7Bbmatrix%7D%0A10%20%5Ctextup%7B%20cups%20of%20dough%7D%20%5C%5C%0A2%20%5Ctextup%7B%20cups%20of%20chocolate%20chips%7D%20%5C%5C%0A%5Cend%7Bbmatrix%7D" alt="\vec{v}=\begin{bmatrix}
10 \textup{ cups of dough} \\
2 \textup{ cups of chocolate chips} \\
\end{bmatrix}" />
 
Now, suppose you wanted to convert this into metric measurements (because the units are easier and/or you aren't in upper North America). You could accomplish this with the following expression:

<img src="https://i.upmath.me/svg/%5Ctextup%7Bmetricized%5C%20%7D%5Cvec%7Bv%7D%20%3D%20%5Cbegin%7Bbmatrix%7D%0A250%20%5Cfrac%7B%5Ctextup%7Bml%7D%7D%7B%5Ctextup%7Bcup%7D%7D%20%5Ccdot%2010%20%5Ctextup%7B%20cups%20of%20dough%7D%5C%5C%0A250%20%5Cfrac%7B%5Ctextup%7Bml%7D%7D%7B%5Ctextup%7Bcup%7D%7D%20%5Ccdot%202%5Ctextup%7B%20cups%20of%20chocolate%20chips%7D%5C%5C%0A%5Cend%7Bbmatrix%7D%3D%5Cbegin%7Bbmatrix%7D%0A2500%20%5Ctextup%7B%20ml%20of%20dough%7D%5C%5C%0A500%20%5Ctextup%7B%20ml%20of%20chocolate%20chips%7D%5C%5C%0A%5Cend%7Bbmatrix%7D" alt="\textup{metricized\ }\vec{v} = \begin{bmatrix}
250 \frac{\textup{ml}}{\textup{cup}} \cdot 10 \textup{ cups of dough}\\
250 \frac{\textup{ml}}{\textup{cup}} \cdot 2\textup{ cups of chocolate chips}\\
\end{bmatrix}=\begin{bmatrix}
2500 \textup{ ml of dough}\\
500 \textup{ ml of chocolate chips}\\
\end{bmatrix}" />

By using the transformation <img src="https://i.upmath.me/svg/%5Cmathbf%7BM%7D_1%3D%5Cbegin%7Bbmatrix%7D%0A250%20%5Cfrac%7B%5Ctextup%7Bml%7D%7D%7B%5Ctextup%7Bcup%7D%7D%20%26%200%5C%5C%0A0%20%20%26%20250%20%5Cfrac%7B%5Ctextup%7Bml%7D%7D%7B%5Ctextup%7Bcup%7D%7D%5C%5C%20%0A%5Cend%7Bbmatrix%7D" alt="\mathbf{M}_1=\begin{bmatrix}
250 \frac{\textup{ml}}{\textup{cup}} &amp; 0\\
0  &amp; 250 \frac{\textup{ml}}{\textup{cup}}\\ 
\end{bmatrix}" />, you can achieve the same result via

<img src="https://i.upmath.me/svg/%5Cbegin%7Balign*%7D%0A%5Ctextup%7Bmetricized%5C%20%7D%5Cvec%7Bv%7D%20%26%3D%20%5Cmathbf%7BM%7D_1%20%5Cvec%7Bv%7D%20%5C%5C%0A%26%3D%5Cbegin%7Bbmatrix%7D%0A250%20%5Cfrac%7B%5Ctextup%7Bml%7D%7D%7B%5Ctextup%7Bcup%7D%7D%20%26%200%5C%5C%0A0%20%20%26%20250%20%5Cfrac%7B%5Ctextup%7Bml%7D%7D%7B%5Ctextup%7Bcup%7D%7D%5C%5C%20%0A%5Cend%7Bbmatrix%7D%5Cbegin%7Bbmatrix%7D%0A10%20%5Ctextup%7B%20ml%20of%20dough%7D%5C%5C%0A2%20%5Ctextup%7B%20ml%20of%20chocolate%20chips%7D%5C%5C%0A%5Cend%7Bbmatrix%7D%3D%5Cbegin%7Bbmatrix%7D%0A2500%20%5Ctextup%7B%20ml%20of%20dough%7D%5C%5C%0A500%20%5Ctextup%7B%20ml%20of%20chocolate%20chips%7D%5C%5C%0A%5Cend%7Bbmatrix%7D%0A%5Cend%7Balign%7D" alt="\begin{align*}
\textup{metricized\ }\vec{v} &amp;= \mathbf{M}_1 \vec{v} \\
&amp;=\begin{bmatrix}
250 \frac{\textup{ml}}{\textup{cup}} &amp; 0\\
0  &amp; 250 \frac{\textup{ml}}{\textup{cup}}\\ 
\end{bmatrix}\begin{bmatrix}
10 \textup{ ml of dough}\\
2 \textup{ ml of chocolate chips}\\
\end{bmatrix}=\begin{bmatrix}
2500 \textup{ ml of dough}\\
500 \textup{ ml of chocolate chips}\\
\end{bmatrix}
\end{align}" />

In this way, we can transform data with matrices. You might notice that we transformed each piece individually - that is, the transformed cookie dough amount only relied on the original cookie dough amount, and the transformed chocolate chip amount only relied on the original chocolate chip amount. This is what's known as a _scaling transformation_ - we can do more than that, though.

Suppose Darcy only wants cookies where there is at least > 10% chocolate chips by volume prior to baking, and the more chocolate chips, the better (they are a chocolate chip fanatic). We might come up with a "Darcy score", <img src="https://i.upmath.me/svg/D(%5Cvec%7Bx%7D)" alt="D(\vec{x})" /> that takes in a chocolate chip cookie composition and outputs how much Darcy likes it. In this case, if we wanted positive scores to be "cookies Darcy likes", we could go through the process of

<img src="https://i.upmath.me/svg/%5Ctextup%7Bneed%20%7D%20%5Cvec%7Bx%7D_%7Bchocolate%7D%20%3E%200.1(%5Cvec%7Bx%7D_%7Bchocolate%7D%20%2B%20%5Cvec%7Bx%7D_%7Bdough%7D)%20%5C%5C%0A%20%20%5CRightarrow%5Ctextup%7Bneed%20%7D%20%5Cvec%7Bx%7D_%7Bchocolate%7D%20-%200.1(%5Cvec%7Bx%7D_%7Bchocolate%7D%20%2B%20%5Cvec%7Bx%7D_%7Bdough%7D)%20%3E%200%20%5C%5C%0A%20%20%5CRightarrow%5Ctextup%7Bneed%20%7D%200.9%5Cvec%7Bx%7D_%7Bchocolate%7D%20-%200.1%5Cvec%7Bx%7D_%7Bdough%7D%3E0" alt="\textup{need } \vec{x}_{chocolate} &gt; 0.1(\vec{x}_{chocolate} + \vec{x}_{dough}) \\
  \Rightarrow\textup{need } \vec{x}_{chocolate} - 0.1(\vec{x}_{chocolate} + \vec{x}_{dough}) &gt; 0 \\
  \Rightarrow\textup{need } 0.9\vec{x}_{chocolate} - 0.1\vec{x}_{dough}&gt;0" />

To obtain a Darcy Chocolate Chip Cookie score(TM) of

<img src="https://i.upmath.me/svg/D(%5Cvec%7Bx%7D)%3D0.9%5Cvec%7Bx%7D_%7Bchocolate%7D%20-%200.1%5Cvec%7Bx%7D_%7Bdough%7D" alt="D(\vec{x})=0.9\vec{x}_{chocolate} - 0.1\vec{x}_{dough}" />

This is what's known as a _linear combination_ - the result depends only on adding multiples of the cookie dough and the chocolate chips - and the transformation can be represented in matrix form.

<img src="https://i.upmath.me/svg/%5Cmathbf%7BD%7D%3D%5Cbegin%7Bbmatrix%7D%0A-0.1%20%26%200.9%5C%5C%0A%5Cend%7Bbmatrix%7D" alt="\mathbf{D}=\begin{bmatrix}
-0.1 &amp; 0.9\\
\end{bmatrix}" />

And so we have

<img src="https://i.upmath.me/svg/D(%5Cvec%7Bx%7D)%3D%20%5Cmathbf%7BD%7D%5Cvec%7Bx%7D" alt="D(\vec{x})= \mathbf{D}\vec{x}" />

We will elaborate on these topics and more in the sections below.

\*Apparently Commonwealth cups and American cups are different? I wonder if I've been preparing food wrong lately :p.
## Linear Combinations
### Span
### Basis Vectors
### Null Space

## Linear Transformations
### What are Linear Transformations?
#### Intuitively
Intuitively, a linear transformation is one that, if applied to a coordinate space, **preserves lines**, **preserves ratios of distances between points**, and that **map the origin to itself**. If any one of these is violated, the transformation is not linear. As an example, any transformation that translates the vector (0, 0) is not linear.
#### Formally
Formally, a linear transformation _T_: *V* ⭢ *W* (where _V_ and _W_ are real vector spaces) is any transformation that satisfies the following two axioms:
|   |   |   |
|---|---|---|
| **Additivity** | <img src="https://i.upmath.me/svg/L(%5Cvec%7Bv%7D_1%2B%5Cvec%7Bv%7D_2)%3DL(%5Cvec%7Bv%7D_1)%2BL(%5Cvec%7Bv%7D_2)" alt="L(\vec{v}_1+\vec{v}_2)=L(\vec{v}_1)+L(\vec{v}_2)" /> &nbsp;&nbsp;| <img src="https://i.upmath.me/svg/%5Cforall%20%5Cvec%7Bv%7D_1%2C%20%5Cvec%7Bv%7D_2%20%5Cin%20V" alt="\forall \vec{v}_1, \vec{v}_2 \in V" /> |
| **Homogeneity** | <img src="https://i.upmath.me/svg/L(r%5Cvec%7Bv%7D)%3DrL(%5Cvec%7Bv%7D)" alt="L(r\vec{v})=rL(\vec{v})" /> |<img src="https://i.upmath.me/svg/%5Cforall%20%5Cvec%7Bv%7D%20%5Cin%20V%2C%20r%5Cin%20%5CR" alt="\forall \vec{v} \in V, r\in \R" />

### Examples
Below are the fundamental 2D linear transformations/matrices
#### Identity
The identity transformation takes in a vector and spits out the same vector. The matrix is

<img src="https://i.upmath.me/svg/I%3D%5Cbegin%7Bbmatrix%7D%0A1%20%26%200%20%5C%5C%0A0%20%26%201%20%5C%5C%0A%5Cend%7Bbmatrix%7D" alt="I=\begin{bmatrix}
1 &amp; 0 \\
0 &amp; 1 \\
\end{bmatrix}" />. 

You might notice that I'm mixing the terms matrix and transformation a bit - the identity matrix is _I_ as given above, and the identity transformation on a vector is just multiplying the matrix by that vector: <img src="https://i.upmath.me/svg/I(%5Cvec%7Bv%7D)%3D%5Cbegin%7Bbmatrix%7D%0A1%20%26%200%20%5C%5C%0A0%20%26%201%20%5C%5C%0A%5Cend%7Bbmatrix%7D%5Cvec%7Bv%7D" alt="I(\vec{v})=\begin{bmatrix}
1 &amp; 0 \\
0 &amp; 1 \\
\end{bmatrix}\vec{v}" /> (which is just <img src="https://i.upmath.me/svg/%5Cvec%7Bv%7D" alt="\vec{v}" />). 
#### Scaling, Reflection, Rotation, Shearing, and Projection
|&nbsp;|&nbsp;|&nbsp;|&nbsp;|
|--|--|--|--|
|Scaling|<img src="https://i.upmath.me/svg/%5Cbegin%7Bbmatrix%7Dx%20%26%200%20%5C%5C0%20%26%20y%20%5C%5C%5Cend%7Bbmatrix%7D" alt="\begin{bmatrix}x &amp; 0 \\0 &amp; y \\\end{bmatrix}" />| |Scaling matrices scale a vector along the direction of the vector space's basis vectors (the vectors corresponding to the coordinates being used - i.e. (0, 1) and (1,0) in many 2D-cases).|
|Reflection|<img src="https://i.upmath.me/svg/%5Ctext%7BRef%7D(%5Ctheta)%3D%5Cbegin%7Bbmatrix%7Dx%20%26%200%20%5C%5C0%20%26%20y%20%5C%5C%5Cend%7Bbmatrix%7D" alt="\text{Ref}(\theta)=\begin{bmatrix}x &amp; 0 \\0 &amp; y \\\end{bmatrix}" />| |Reflection mirrors a vector across a line going through the origin. Only reflections across lines going through the origin are linear transformations (although all are affine transforms; more on that later)|



**TODO**




## Beyond Linear Transformations: Affine Transformations
FOr this course, 
