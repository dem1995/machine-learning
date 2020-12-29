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

## Motivating Example

Now, suppose we're dealing with chocolate-chip cookies, and we want to encode information about the chocolate chips and cookie dough used. We might care about the volume, that is, how many cups\* of each we have. Suppose in our last batch of cookies we used 10 cups of dough and 2 cups of chocolate-chip cookies. We might represent this, then, as

<img src="https://i.upmath.me/svg/%5Cvec%7Bv%7D%3D%5Cbegin%7Bbmatrix%7D%0A10%20%5Ctextup%7B%20cups%20of%20dough%7D%20%5C%5C%0A2%20%5Ctextup%7B%20cups%20of%20chocolate%20chips%7D%20%5C%5C%0A%5Cend%7Bbmatrix%7D" alt="\vec{v}=\begin{bmatrix}
10 \textup{ cups of dough} \\
2 \textup{ cups of chocolate chips} \\
\end{bmatrix}" />
 
Now, suppose you wanted to convert this into metric measurements (because the units are easier and/or you aren't in upper North America). You could accomplish this with the

## Linear Transformations
### What are Linear Transformations?
#### Intuitively
Intuitively, a linear transformation is one that, if applied to a coordinate space, **preserves lines**, **preserves ratios of distances between points**, and that **map the origin to itself**. If any one of these is violated, the transformation is not linear. As an example, any transformation that translates the vector (0, 0) is not linear.
#### Formally
Formally, a linear transformation _T_: *V* ⭢ *W* (where _V_ and _W_ are real vector spaces) is any transformation that satisfies the following two axioms:
|&nbsp;|&nbsp;|&nbsp;|
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
#### Scaling
Scaling matrices 
#### Reflection
#### Rotation
#### Shearing
###

## Beyond Linear Transformations
FOr this course, 
