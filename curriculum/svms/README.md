---
layout: default
title: Support Vector Machines
parent: Curriculum
nav_order: 10
---

### External Resources
- [Kilian Weinberger's SVM Lecture Notes](https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote09.html) An unequivocally-good, concise, comprehensive look at SVMs. Less gradual than the two resources below, but on the flipside very to-the-point. As far as personal opinions go,  I think it would really have behoven me to have searched a little more and stumbled across this before I got to the editing phase for this article
- [Support Vector Machines (SVM) — An Overview](https://towardsdatascience.com/https-medium-com-pupalerushikesh-svm-f4b42800e989) provides a good overview of SVMs/parameters, as well as a straightforward example of a kernel transformation
- [Support Vector Machines explained with Python examples](https://towardsdatascience.com/support-vector-machines-explained-with-python-examples-cb65e8172c85/) provides a more in-depth exploration of SVMS and some of the math, as well as providing some good Python examples


# Support Vector Machines
## Introduction
The basic premise behind Support Vector Machines (SVMs) is that they provide a **supervised method for finding an efficient binary classifier**. Specifically, given a set of labelled vectors in *n* dimensions, we **find a line/plane** (linear equation) in *n*-1 dimensions **that best partitions our vectors**.

We will start by talking about maximum/hard-margin SVMs, used for data that is linearly separable, i.e. that can be split by a line. A more comprehensive introduction to linear separability can be found under [Linear Classifiers](https://dem1995.github.io/machine-learning/curriculum/linear_classifiers/linear_classifiers_overview.html#external-resources), if desired. We will then talk about an extension of them that can be used for non-linearly-separable data.

## Maximum-margin SVMs
### Motivating Example
To give an example, we might have red (square) vectors and blue (circle) vectors, and desire a simple way of determining what's what. The green line/hyperplane in the below image splits them in twain, and we can thus **derive an expression** that **takes in a vector** and **results in different labels** - negative values on one side of the line and positive values on the other.

![separating boundary image](https://raw.githubusercontent.com/dem1995/algorithms/main/svms/separating_boundary.png?style=centered)

For example, one might imagine the equation of the line here is some <img src="https://i.upmath.me/svg/%5Cvec%7Bw%7D%5Ccdot%5Cvec%7Bx%7D%20-%20b%20%3D%200" alt="\vec{w}\cdot\vec{x} - b = 0" /> - in that case, we can let our classifier function be <img src="https://i.upmath.me/svg/%5Ctexttt%7Bsgn%7D(%5Cvec%7Bw%7D%5Ccdot%5Cvec%7Bx%7D%20-%20b)" alt="\texttt{sgn}(\vec{w}\cdot\vec{x} - b)" />, resulting in -1 for vectors below the line and +1 for vectors above the line. 

### Choice-of-Hyperplane Intuition
In the previous example, the demonstrated line actually is the result of running a support vector machine. But why that line? Consider the example again, at left, and the figure at right.

![separating boundary image](https://raw.githubusercontent.com/dem1995/algorithms/main/svms/separating_boundary_no_support_vectors_shown.png) ![nonoptimal separating boundaries image](https://raw.githubusercontent.com/dem1995/algorithms/main/svms/separating_boundaries_nonoptimal_v2.png)

All of these green lines separate the vectors properly, and indeed could all be used to generate equations for determining the vectors. The line on the left, though, maximizes the distance to the closest sample in each class, and so **typically generalizes best to out-of-sample data**. 

Sure, we could have some wonky underlying distribution, such as where the circles actually appear really close to the squares (or even within the cavity of the squares), but with the information we _know_ (i.e. our collection of samples) additional justification would be needed for choosing anything but this line.

Looking at the line again, we've highlighted the closest vectors, known as the **_support vectors_** as well as indicated what we mean when we say "maximizing the distance to the closest sample in each class", also known as the **_margin_**.

![maximizing margin image](https://raw.githubusercontent.com/dem1995/algorithms/main/svms/maximum_margin.png)

### Support Vector Intuition
Notice that, as the optimal hyperplane is that which separates the classes and maximizes the margin to the closest vectors (aka the support vectors), **the optimal hyperplane is entirely defined by the support vectors**. The support vectors are alternatively given as the collection of vectors that **lie on the margin boundary** (take a moment to convince yourself that these are the same).

### Maximum-margin Hyperplane Equation
The maximum-margin hyperplane equations out there can seem a little opaque, so we'll build it up intuitively. Recall that our goal is to select a line/plane that maximizes the margin about it, that is, a line/plane that is the furthest from any of the datapoints subject to separating them. The format for the equation for this, then, is

<img src="https://i.upmath.me/svg/%5Ctextup%7BLine%2Fplane%20with%20greatest%20distance%20to%20datapoints%7D%20%5Ctextit%7B%20that%7D%20%5Ctextup%7B%20separates%20the%20classes%7D" alt="\textup{Line/plane with greatest distance to datapoints} \textit{ that} \textup{ separates the classes}" />

For the purposes of the equation, we formalize our set of inputs-output pairs as <img src="https://i.upmath.me/svg/%5C%7B(%5Cvec%7Bx%7D_i%2C%20y_i)%5C%7D" alt="\{(\vec{x}_i, y_i)\}" />, where <img src="https://i.upmath.me/svg/%5Cvec%7Bx_i%7D%5Cin%20%5CR%5Ed" alt="\vec{x_i}\in \R^d" /> and (giving the output labels values of -1 and 1 for the sake of computation) <img src="https://i.upmath.me/svg/y%5Cin%5C%7B-1%2C%201%5C%7D" alt="y\in\{-1, 1\}" />. 

Finding the maximum-margin hyperplane described by some line/plane <img src="https://i.upmath.me/svg/P%20%3D%20%5C%7B%5Cvec%7Bx%7D%5Cin%20%5CR%5Ed%20%5Ctextit%7B%20such%20that%20%7D%20%5Cvec%7Bw%7D%5ET%20%5Cvec%7Bx%7D%3D0%5C%7D" alt="P = \{\vec{x}\in \R^d \textit{ such that } \vec{w}^T \vec{x}=0\}" /> then becomes

<img src="https://i.upmath.me/svg/%20%0A(%5Cvec%7Bw%7D%5E*%2C%20b%5E*)%3D%20%5Cunderbrace%7B%0A%20%20%20%5Carg%5Cmax_%7B%5Cvec%7Bw%7D%2C%20b%7D%5Chspace%7B6%7D%20%0A%20%20%20%5Cunderbrace%7B%0A%20%20%20%5Cmin_%7Bi%7D%0A%20%20%20%20%20%20%20%5Cfrac%7B%5Cleft%7C%5Cvec%7Bw%7D%5ET%5Cvec%7Bx%7D_i%20%2B%20b%5Cright%7C%7D%20%7B%5C%7C%5Cvec%7Bw%7D%5C%7C%7D%20%20%20%20%0A%20%20%20%7D_%0A%20%20%20%7B%0A%20%20%20%20%20%20%5Ctextup%7Bdistance%20to%20closest%20%7D%20%5Cvec%7Bx_i%7D%20%5Ctextup%7B%20vector%7D%0A%20%20%20%7D%0A%7D_%0A%7B%0A%20%20%20%5Ctextup%7BMargin%20that%20maximimizes%20distances%20to%20vectors%7D%0A%7D%20%5Ctextit%7Bsuch%20that%20%7D%20%5Cunderbrace%7B%0A%5Cforall%20i%2C%20%5C%20y_i(%5Cvec%7Bw%7D%5ET%5Cvec%7Bx%7D_i%2Bb)%0A%7D_%0A%7B%5Ctextup%7BThe%20hyperplane%20is%20separating%7D%0A%7D" alt=" 
(\vec{w}^*, b^*)= \underbrace{
   \arg\max_{\vec{w}, b}\hspace{6} 
   \underbrace{
   \min_{i}
       \frac{\left|\vec{w}^T\vec{x}_i + b\right|} {\|\vec{w}\|}    
   }_
   {
      \textup{distance to closest } \vec{x_i} \textup{ vector}
   }
}_
{
   \textup{Margin that maximimizes distances to vectors}
} \textit{such that } \underbrace{
\forall i, \ y_i(\vec{w}^T\vec{x}_i+b)
}_
{\textup{The hyperplane is separating}
}" />

The problem of finding which then boils down through some very nontrivial simplifications to

<img src="https://i.upmath.me/svg/%20%0A(%5Cvec%7Bw%7D%5E*%2C%20b%5E*)%3D%20%5Cunderbrace%7B%0A%20%20%20%5Carg%5Cmin_%7B%5Cvec%7Bw%7D%7D%20%5C%7C%5Cvec%7Bw%7D%5C%7C%0A%7D_%0A%7B%0A%20%20%20%5Ctextup%7BMargin%20that%20maximimizes%20distances%20to%20vectors%7D%0A%7D%20%5Ctextit%7Bsuch%20that%20%7D%20%5Cunderbrace%7B%0A%5Cforall%20i%2C%20%5C%20y_i(%5Cvec%7Bw%7D%5ET%5Cvec%7Bx%7D_i%2Bb)%0A%7D_%0A%7B%5Ctextup%7BThe%20hyperplane%20is%20separating%7D%0A%7D" alt=" 
(\vec{w}^*, b^*)= \underbrace{
   \arg\min_{\vec{w}} \|\vec{w}\|
}_
{
   \textup{Margin that maximimizes distances to vectors}
} \textit{such that } \underbrace{
\forall i, \ y_i(\vec{w}^T\vec{x}_i+b)
}_
{\textup{The hyperplane is separating}
}" />


## Soft-Margin SVMs (for non-linearly-separable data)
Not all data is linearly separable, however. **For data that isn't linearly-separable, maximizing the margin does not necessarily minimize the error**. To accommodate for this, soft-margin SVMs use what's called a **slack parameter**, _**C**_, that can be tweaked to prioritize how much we want to **_maximize the margin_ versus how much we want to _minimize the error_**.


Now, you might be asking at this point what the meaning of a margin even is if there's no separating hyperplane. To address this, we use the equation we derived earlier as a description of "maximum margin"-ness and penalize the result using the error by a factor of *C*.

### Soft-Margin Hyperplane Equation
<img src="https://i.upmath.me/svg/%5Cbegin%7Balign*%7D%0A%09(%20%5Cvec%7Bw%7D%5E*%2C%20b%5E*%2C%20%20%5Cvec%7B%5Cxi%7D%5E*)%20%3D%20%5Carg%5Cmin_%7B%20%5Cvec%7Bw%7D%5Cin%5CR%5Ed%2C%20b%5Cin%5CR%2C%20%20%5Cvec%7B%5Cxi%7D%5Cin%5CR%5EN%7D%20%5C%20%26%20%5Cfrac%7B1%7D%7B2%7D%20%5C%7C%20%5Cvec%7Bw%7D%5C%7C%5E2%20%2B%20C%5Csum_%7Bi%3D1%7D%5EN%20%5Cxi_i%20%5C%5C%0A%09%09%09%09%09%5Cmbox%7Bs.t.%20%7D%5C%20%26%20y_i(%5Cinner%7B%20%5Cvec%7Bw%7D%5ET%7D%7B%20x_i%7D%20%2B%20b)%20-%20%5Cxi_i%20%2C%20%5Cquad%20i%3D1%2C%5Cdots%2CN%20.%5C%5C%0A%09%09%09%09%09%26%20%5Cxi_i%0A%5Cend%7Balign*%7D" alt="\begin{align*}
	( \vec{w}^*, b^*,  \vec{\xi}^*) = \arg\min_{ \vec{w}\in\R^d, b\in\R,  \vec{\xi}\in\R^N} \ &amp; \frac{1}{2} \| \vec{w}\|^2 + C\sum_{i=1}^N \xi_i \\
					\mbox{s.t. }\ &amp; y_i(\inner{ \vec{w}^T}{ x_i} + b) - \xi_i , \quad i=1,\dots,N .\\
					&amp; \xi_i
\end{align*}" />

Okay, so I lied a little bit by virtue of neglecting to mention ξ. However, letting *C* ≥ 0, you can ignore ξ (minor COVID-19 perk- I don't need to write this for you all on a whiteboard*) and convert this into

<img src="https://i.upmath.me/svg/%5Cbegin%7Balign*%7D(%5Cvec%7Bw%7D%5E*%2C%20b%5E*)%20%3D%20%0A%5Cunderbrace%7B%0A%20%20%20%5Carg%5Cmin_%7B%5Cvec%7Bw%7D%5Cin%5CR%5Ed%2C%20b%5Cin%5CR%7D%20%5Cfrac%7B1%7D%7B2%7D%20%5C%7C%5Cvec%7Bw%7D%5C%7C%5E2%0A%7D_%7B%5Ctextup%7BMaximizing%20margin%7D%7D%20%5C%20%2B%20%5C%20%0AC%5Cunderbrace%7B%5Csum_%7Bi%3D1%7D%5EN%20%5Cbegin%7Barray%7D%7Bcc%7D%0A%5C%201-y_%7Bi%7D(%5Cmathbf%7Bw%7D%5ET%20%5Cmathbf%7Bx%7D_%7Bi%7D%2Bb)%20%26%20%5Ctextrm%7B%20if%20%24y_%7Bi%7D(%5Cmathbf%7Bw%7D%5ET%20%5Cmathbf%7Bx%7D_%7Bi%7D%2Bb)%3C1%24%7D%5C%5C%0A0%20%26%20%5Ctextrm%7B%20if%20%24y_%7Bi%7D(%5Cmathbf%7Bw%7D%5ET%20%5Cmathbf%7Bx%7D_%7Bi%7D%2Bb)%24%7D%0A%5Cend%7Barray%7D%7D_%7B%5Ctextup%7BPenalization%2Floss%20due%20to%20errors%7D%7D%0A%5Cend%7Balign*%7D" alt="\begin{align*}(\vec{w}^*, b^*) = 
\underbrace{
   \arg\min_{\vec{w}\in\R^d, b\in\R} \frac{1}{2} \|\vec{w}\|^2
}_{\textup{Maximizing margin}} \ + \ 
C\underbrace{\sum_{i=1}^N \begin{array}{cc}
\ 1-y_{i}(\mathbf{w}^T \mathbf{x}_{i}+b) &amp; \textrm{ if $y_{i}(\mathbf{w}^T \mathbf{x}_{i}+b)&lt;1$}\\
0 &amp; \textrm{ if $y_{i}(\mathbf{w}^T \mathbf{x}_{i}+b)$}
\end{array}}_{\textup{Penalization/loss due to errors}}
\end{align*}" />

Which then can be written as

<img src="https://i.upmath.me/svg/%5Cbegin%7Balign*%7D(%5Cvec%7Bw%7D%5E*%2C%20b%5E*)%20%5Chspace%7B5%7D%3D%5Chspace%7B20%7D%20%0A%5Cunderbrace%7B%0A%20%20%20%5Carg%5Cmin_%7B%5Cvec%7Bw%7D%5Cin%5CR%5Ed%2C%20b%5Cin%5CR%7D%20%5Cfrac%7B1%7D%7B2%7D%20%5C%7C%20%5Cvec%7Bw%7D%5C%7C%5E2%0A%7D_%7B%5Ctextup%7BMaximizing%20margin%7D%7D%20%5Chspace%7B30%7D%2B%20%0A%5C%20C%5Cunderbrace%7B%5Csum_%7Bi%3D1%7D%5EN%20%5Cmax(1-y_%7Bi%7D(%5Cmathbf%7Bw%7D%5ET%20%5Cmathbf%7Bx%7D_%7Bi%7D%2Bb)%2C%5C%200)%0A%7D_%7B%5Ctextup%7B%60%60Hinge%20loss''%2C%20penalization%20due%20to%20errors%7D%7D%0A%5Cend%7Balign*%7D" alt="\begin{align*}(\vec{w}^*, b^*) \hspace{5}=\hspace{20} 
\underbrace{
   \arg\min_{\vec{w}\in\R^d, b\in\R} \frac{1}{2} \| \vec{w}\|^2
}_{\textup{Maximizing margin}} \hspace{30}+ 
\ C\underbrace{\sum_{i=1}^N \max(1-y_{i}(\mathbf{w}^T \mathbf{x}_{i}+b),\ 0)
}_{\textup{``Hinge loss'', penalization due to errors}}
\end{align*}" />


*![A meme about how hard the Greek letter Xi is to write](simpsons_xi.png)
