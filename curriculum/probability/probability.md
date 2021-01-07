---
layout: default
title: Probability
parent: Curriculum
nav_order: 1
---


# Probability
## Part 1: Fundamentals
### Samples and Events
Probability deals with _outcomes_, the results that can and do happen in our world. We'll give some formal definitions to begin with, then flesh them out with a real-world example.

#### Definitions
Formally, we refer to tiny discrete outcomes as **samples**.  We refer to collections of those samples as **events**. Samples are drawn from the set of all samples, the **sample space Ω**; events are drawn from the set of all events, the **event space ℰ**, and, as events are just collections of outcomes, ℰ = set of all possible sets of samples, 𝒫(Ω), the power set of Ω.

#### Example
As an example, suppose you're rolling a six-sided dice. The samples space here is Ω=`{1, 2, 3, 4, 5, 6}`. The event space, meanwhile, is all the ways you could get some number of these samples - ℰ=`{ {}, {1}, {2}, {3}, ..., {1, 2}, {1, 3}, ..., {1, 2, 3, 4, 5, 6} }`. **By focusing on the event space, this not only lets us talk about "hey, look, I rolled a 3" - the event {3} - but also more complicated situations, like "hey, look, I rolled an even number" - the event {2, 4, 6}.**

#### Axioms
The event space ℰ must satisfy that

1. If an event A is in ℰ, then Aᶜ is in ℰ. In other words, &nbsp;&nbsp; <img src="https://i.upmath.me/svg/A%20%5Cin%20%5Cmathcal%20E%20%5CRightarrow%20A%5Ec%20%5Cin%20%5Cmathcal%20E" alt="A \in \mathcal E \Rightarrow A^c \in \mathcal E" />
2. If a collection of events A₁, A₂... is in ℰ, then the set of all their constituent samples ∪(A₁, A₂...) is an event in ℰ. In other words, &nbsp;&nbsp; <img src="https://i.upmath.me/svg/A_1%2C%20A_2%2C%20...%20%5Cin%20%5Cmathcal%20E%20%5CRightarrow%20%5Cleft(%5Cbigcup%20A_1%2C%20A_2%20...%5Cright)%20%5Cin%20%5Cmathcal%20E%22" alt="A_1, A_2, ... \in \mathcal E \Rightarrow \left(\bigcup A_1, A_2 ...\right) \in \mathcal E&quot;" />
3. There is at least one event. In other words, <img src="https://i.upmath.me/svg/%7C%5Cmathcal%20E%7C%3E0" alt="|\mathcal E|&gt;0" />

A space (Ω, ℰ) is known as a **measurable space**.

#### Example 2: Electric (Burnout) Boogaloo

Suppose we are owners of a "Braum's Ice Cream" shop (a popular chain in Oklahoma, USA), and we have a large neon sign in front of our store.

![Neon "Braum's Ice Cream" sign. The letters B R A U M and S are lit up](braums_correct.jpg "Lit-up Braum's Ice Cream Sign"){:height="200px" width="200px"}

If we consider the outcomes of our lights going out, we have a sample space Ω=`{B R A U M S}`, with each letter corresponding to the light going out. Our events would then be which collection of lights go out - naturally, for example, if we have the event `A={R A U M S}`, we just have 'B Ice Cream and Dairy Store'. There are certain events we naturally want to avoid - for example, the event `A={B A M S} = {R U M}ᶜ` - the event where the letters B, A, M, and S go out, or the *complement* of the event where R, U, and M go out - would just leave us with 'RUM Ice Cream and Dairy Store'. A similar unfortunate event is given below.

![Neon "Braum's Ice Cream" sign. The letters B R and A are lit up](braums_incorrect.jpg "Lit-up Braum's Ice Cream Sign fail"){:height="200px" width="200px"}

Exercise: briefly think through what the sample space/event space would be for the lights of a a Snap Fitness™ location (and what events you might want to avoid if you were responsible for it).

![Neon "Snap Fitness" sign. The letters N A and P are lit up, followed by "Fitness"](nap_fitness.png "Lit-up Snap Fitness Sign fail"){:height="200px" width="200px"}

### Probability Distributions
Another example of having an event space is that it allows us to derive probabity distributions. A **probability distribution** is, formally, a function P:ℰ⟶\[0, 1\] from events to the range 0-1 inclusive if
* <img src="https://i.upmath.me/svg/P(%5COmega)%3D1" alt="P(\Omega)=1" /> (the probability of any of the samples occurring is 1)
* <img src="https://i.upmath.me/svg/%5Cforall%20A_1%2C%20A_2%5Cin%20%5Cmathcal%20E%2C%20(A_1%5Ccap%20A_2%20%3D%20%5Cemptyset)%20%5CRightarrow%20P(A_1%20%5Ccup%20A_2)%20%3D%20P(A_1)%20%2B%20P(A_2)" alt="\forall A_1, A_2\in \mathcal E, (A_1\cap A_2 = \emptyset) \Rightarrow P(A_1 \cup A_2) = P(A_1) + P(A_2)" /> (for two disjoint events, the probability that any of their aggregate samples occur (the probability either event occurs) is the same as the sum of the probabilities of the two events)

In the context of our previous die example, consider the event "the die roll is 2 or less" - `A₁={1, 2}` - and the event "the die roll is 5 or more" - `A₂={5, 6}`. The second property tells us that, since `A₁ ∩ A₂ = {}`, P(A₁) + P(A₂) = P(A₁ ∪ A₂). **In other words, the second property tells us that P("getting a die roll ≤ 2 or a die roll 	≥ 5") = P("getting a die roll ≤ 2") + P("getting a die roll ≥ 5")**. 

The first property, on the other hand, just tells us that the event "the die roll is 1, 2, 3, 4, 5, or 6" is 100% likely to happen.

These properties can be readily used to derive other facts about probability distributions as well - such as that P(Aᶜ) = 1-P(A).

### Probability Mass & Density Functions

### Expected Values
### Independence and Effective Independence
### Product Rule and Bayes's Theorem
## Part 2: Applications
