---
layout: default
title: Vector Dot Product Intuition
parent: Extra Pages
nav_order: 1.5
---

# Vector Dot Product Intuition
## Page Purpose
This page is designed to give intuition to the vector dot product (written for vectors **u** and **v** as **u**⋅**v**, or effectively via matrix multiplication as **u**ᵀ**v** or as an inner product ⟨**u**, **v**⟩). The phrase

"The dot product of **u** and **v** is just **the degree by which each are in the same direction, scaled by their actual lengths**."

is the important takeaway here; the rest of the information on this page exists to clarify exactly why that is/ give examples and visual intuition.

## Overview
The dot product of **u** and **v** is given by

<img src="https://i.upmath.me/svg/%5Cmathbf%7Bu%7D%20%5Ccdot%20%5Cmathbf%7Bv%7D%20%3D%20%5Ctextup%7Bcos%7D(%5Ctheta_%7B%5Cmathbf%7Bu%7D%2C%20%5Cmathbf%7Bv%7D%7D)%20%5Cleft%20%5C%7C%20%5Cmathbf%7Bu%7D%20%5Cright%20%5C%7C%20%5Cleft%20%5C%7C%20%5Cmathbf%7Bv%7D%20%5Cright%20%5C%7C" alt="\mathbf{u} \cdot \mathbf{v} = \textup{cos}(\theta_{\mathbf{u}, \mathbf{v}}) \left \| \mathbf{u} \right \| \left \| \mathbf{v} \right \|" />

In other words, the dot product of **u** and **v** is just **the degree by which each are in the same direction, scaled by their actual lengths**.

This, intuitively, ranges from 0 (when they are perpendicular) to **\|u\|\|v\|** (when they are codirectional) to **--\|u\|\|v\|** (when they are antidirectional).


## Via scalar projections
Put another way,\
<img src="https://i.upmath.me/svg/%5Cmathbf%7Bu%7D%20%5Ccdot%20%5Cmathbf%7Bv%7D%20%3D%20u_%5Cmathbf%7Bv%7D%20%5Cleft%20%5C%7C%20%5Cmathbf%7Bv%7D%20%5Cright%20%5C%7C" alt="\mathbf{u} \cdot \mathbf{v} = u_\mathbf{v} \left \| \mathbf{v} \right \|" />, where <img src="https://i.upmath.me/svg/u_%5Cmathbf%7Bv%7D" alt="u_\mathbf{v}" /> is the scalar projection of **u** onto **v**\
<img src="https://i.upmath.me/svg/%5Cmathbf%7Bu%7D%20%5Ccdot%20%5Cmathbf%7Bv%7D%20%3D%20v_%5Cmathbf%7Bu%7D%20%5Cleft%20%5C%7C%20%5Cmathbf%7Bu%7D%20%5Cright%20%5C%7C" alt="\mathbf{u} \cdot \mathbf{v} = v_\mathbf{u} \left \| \mathbf{u} \right \|" />, where <img src="https://i.upmath.me/svg/v_%5Cmathbf%7Bu%7D" alt="v_\mathbf{u}" /> is the scalar projection of **v** onto **u**

So **u · v** is just the amount of **u** in the direction of **v**, scaled by the magnitude of **v** --- and vice-versa.

As a concrete example of this, consider that the dot product of a vector **A** with a unit vector **û** just gives you the amount of **A** in the direction of **û**, as **û** provides a x1 scaling after scalar projection.\
![The dot product of a vector A with a unit vector û is just A projected onto û's line - the amount of A in the direction of û](https://raw.githubusercontent.com/dem1995/algorithms/main/math/dotproducts/dotprod-seidler-unitprojection.gif?style=centered)

The below image provides some summarizing visual intuition behind the scalar projection's relationship to the dot product. **a · b/||b||** and
|**a**|cos(θ) are both valid ways of writing <img src="https://i.upmath.me/svg/a_%5Cmathbf%7Bb%7D" alt="a_\mathbf{b}" /> (the scalar projection of **a** onto **b**), and multiplying it by **b** so yields the dot product.\
![Dot product intuition](https://raw.githubusercontent.com/dem1995/algorithms/main/math/dotproducts/dotprod-intuition.png?style=centered)

### Via component-wise multiplication dot product definition
The image below provides a derivation of the cosine dot product definition via the component-wise dot product definition.\
![A derivation of the cosine dot product definition via the component-wise dot product definition, from Dr. Seidler's website at the University of Washington from 1998](https://raw.githubusercontent.com/dem1995/algorithms/main/math/dotproducts/dotprod-seidler-derivation.gif?style=centered)

### Interactive
I've created an interactive GeoGebra applet to fiddle around with at https://www.geogebra.org/m/yqnsrnvs.

### Sources
The hand-drawn images for this page were taken from Dr. Seidler's Winter 1998 Phys 121 page at the University of Washington (http://courses.washington.edu/phys121/stuquest/dot.html)
