---
layout: default
title: Support Vector Machines
parent: Curriculum
nav_order: 10
---

### External Resources
- [Support Vector Machines(SVM) — An Overview](https://towardsdatascience.com/https-medium-com-pupalerushikesh-svm-f4b42800e989) provides a good overview of SVMs/parameters, as well as a straightforward example of a kernel transformation
- [Support Vector Machines explained with Python examples](https://towardsdatascience.com/support-vector-machines-explained-with-python-examples-cb65e8172c85/) provides a more in-depth exploration of SVMS and some of the math, as well as providing some good Python examples

# Support Vector Machines

### Introduction
The basic premise behind Support Vector Machines (SVMs) is that they provide a **supervised method for finding an efficient binary classifier**. Specifically, given a set of labelled vectors in *n* dimensions, we **find a line/plane** (linear equation) in *n*-1 dimensions **that best partitions our vectors**. 


### Motivating example
To give an example, we might have red (square) vectors and blue (circle) vectors, and desire a simple way of determining what's what. The green line/hyperplane in the below image splits them in twain, and we can thus **derive an expression** that **takes in a vector** and **results in different labels** - negative values on one side of the line and positive values on the other.

![separating boundary image](https://raw.githubusercontent.com/dem1995/algorithms/main/svms/separating_boundary.png?style=centered)

For example, one might imagine the equation of the line here is some <img src="https://i.upmath.me/svg/%5Cvec%7Bw%7D%5Ccdot%5Cvec%7Bx%7D%20-%20b%20%3D%200" alt="\vec{w}\cdot\vec{x} - b = 0" /> - in that case, we can let our classifier function be <img src="https://i.upmath.me/svg/%5Ctexttt%7Bsgn%7D(%5Cvec%7Bw%7D%5Ccdot%5Cvec%7Bx%7D%20-%20b)" alt="\texttt{sgn}(\vec{w}\cdot\vec{x} - b)" />, resulting in -1 for vectors below the line and +1 for vectors above the line. 

### Choice-of-Hyperplane Intuition
In the previous example, the demonstrated line actually is the result of running a support vector machine. But why that line? Consider the example again, at left, and the figure at right.

![separating boundary image](https://raw.githubusercontent.com/dem1995/algorithms/main/svms/separating_boundary_no_support_vectors_shown.png) ![nonoptimal separating boundaries image](https://raw.githubusercontent.com/dem1995/algorithms/main/svms/separating_boundaries_nonoptimal_v2.png)

All of these green lines separate the vectors properly, and indeed could all be used to generate equations for determining the vectors. The line on the left, though, maximizes the distance to the closest sample in each class, and so **typically generalizes best to out-of-sample data**. 

Sure, we could have some wonky underlying distribution, such as where the circles actually appear really close to the squares (or even within the cavity of the squares), but with the information we _know_ (i.e. our collection of completely-separable samples) additional justification would be needed for choosing anything but this line.

Looking at the line again, we've highlighted the closest vectors, known as the **_support vectors_** as well as indicated what we mean when we say "maximizing the distance to the closest sample in each class", also known as the **_margin_**.

![maximizing margin image](https://raw.githubusercontent.com/dem1995/algorithms/main/svms/maximum_margin.png)

### Support Vector Intuition
Notice that, as the optimal hyperplane is that which separates the classes and maximizes the margin to the closest vectors (aka the support vectors), **the optimal hyperplane is entirely defined by the support vectors**.
