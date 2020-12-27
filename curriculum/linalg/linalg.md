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


  As an example, suppose we wanted to encode information about chocolate chips and cookie dough. 
