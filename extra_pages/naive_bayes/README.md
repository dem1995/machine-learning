---
layout: default
title: Bayesian Thinking & Naïve Bayes Classifiers
parent: Curriculum
mathjax: true
nav_order: 2
---

# Naïve Bayes & Naïve Bayes Classifiers
![Neon lights spelling out Bayes's theorem](bayes_lights.png){: .d-flex	.flex-justify-around}
## Naïve Bayes
### Introduction
When dealing with probability, you're used to making decisions from observing the world around you - how often each side lands face-up on a die, what the proportion of weather you see outside each day, how long a piece of fruit lasts before going bad - but what happens, if, say, you have 5 rolls of a fair die that have happened to all land on '6'?

_Bayes's theorem_ is a way of reconciling some existing understanding of the world - a _prior belief_ - with some observations - _evidence_ - to form more nuanced predictions - a _posterior belief_. Before digging into these terms, let's motivate this a bit with a story.

### Motivation
A group of three friends - Darcy, Edgar, and Fatima -  are at a carnival (in the good timeline, where we're not dealing with a pandemic). A woman comes up to them and tells them she's clairvoyant (she can see things with her mind's eye), and wants to demonstrate it to them by predicting cards of theirs. All three friends are willing to take her up on it - it's good fun, after all!

The woman takes things more seriously than any of them expect, though, and by the end of her preparing and showing precautions they're convinced there's no way she's hiding anything- she's even using the deck Edgar had on him!

The woman deals a card out to each of you, and guesses a 3 of ♥ (hearts), a 5 of ♦ (diamonds), and a jack of ♣ (clubs). Sure enough, these are precisely the cards that Darcy, Edgar, and Fatima are holding! The three tip her generously for her time and convene at a bar to discuss what they just saw.

Now, Darcy, Edgar, and Fatima have had conversations a number of times, and certain trends have popped up.

* Darcy tends to have a very reserved view of the world- they have very strong prior opinions, and casual events don't tend to change those.
 
Before these events, Darcy _knows, with 100% certainty_ "clairvoyance isn't a thing". Darcy's thoughts going into this are what's called their prior, for them, it's effectively infinitely strong. Darcy's prior before seeing this is $$p(\text{"The carnival-woman is clairvoyant})\approx 0$$, and that remains unchanged after her display.
 
* Edgar, on the other hand, has a _very_ open mind - he takes on new viewpoints extremely readily.

Before these events, Edgar believes that "clairvoyance isn't a thing"- but Edgar's opinions flow with the wind and whatever he sees. He effectively has no prior, and takes whatever he sees at face-value - and he just saw someone demonstrate clairvoyance 3/3 times, meaning he 100% believes she was a clairvoyant.

* Finally, Fatima takes a more balanced approach - she has a strong prior, but is open to changing it.

Before these events, Fatima believes that "clairvoyance isn't a thing" - however, with evidence, she's open to the idea the woman /might/ be clairvoyant. Her prior is strong - $$p(\text{The carnival-woman is clairvoyant}) = 1/1000)$$. Unlike Darcy, however, she updates her prior here-

$$
\begin{align*}
&p(\text{The carnival-woman is clairvoyant} | \text{3 right}) \\
&= \frac{p(\text{3 right} | \text{The carnival-woman is clairvoyant}) \cdot p(\text{The carnival-woman is clairvoyant})}{p(\text{3 right})}\\
                                                 &= \frac{1 \cdot \frac{1}{1000}}{p(\text{3 right} | \text{...clairoyant})\cdot p(\text{...clairvoyant}) + p(\text{3 right} | \text{...clairoyant}) \cdot p(\neg\text{...clairvoyant)}}\\
                                                 &= \frac{1 \cdot \frac{1}{1000}}{1 \cdot \frac{1}{1000} + \frac{999}{1000}\frac{1}{52}^{3}}\\
                                                 &\approx \frac{1}{999} 
\end{align*}
$$

![A spectrum from Darcy (infinitely strong prior) to Edgar (infinitely weak prior)](darcyfatimaedgar_spectrum.png)

Fatima obviously had a very strong prior here, but the point is that her viewpoint lies somewhere between Darcy's and Edgar's - she used what she knew before-hand and incorporated her new observations to judge the situation. This is what's known as _Bayesian_ thinking - combining thoughts about some underlying distribution about how the world is set up and incorporating new observations into that expected framework.

### Equation
As mentioned before, _Bayes's theorem_ is a way of reconciling some existing understanding of the world - a _prior belief_ - with some observations - _evidence_ - to form more nuanced predictions - a _posterior belief_.

![A graphic describing Bayes' theorem. P of A given B is denoted as Posterior (for event, given evidence), P of B given A is denoted as Likelihood (of evidence, given event), P(B) is denoted as Prior (for event), and P(B) is denoted as Normalization (probability of evidence)](bayes_theorem_graphic_v2.png)

We're interested in what the probability of some outcome _A_ is given the evidence _B_ we're seeing - to find this, we multipy our _prior_ belief of the outcome A_ by the likelihood of the evidence_ B we're seeing if we assume the outcome _A_ is the case. The division by the probability of our evidence _B_ occurring is relevant for obtaining our actual posterior probability (our prediction), but as we shall see in a bit, for some applications is largely irrelevant.
## Naïve Bayes Classifier


# Acknowledgements
Credit to Dr. Robert Kübler at [A Gentle Introduction to Bayesian Inference](https://towardsdatascience.com/a-gentle-introduction-to-bayesian-inference-6a7552e313cb) for the carnival/funfair setting for explaining Bayesian thinking.

