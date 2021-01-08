---
layout: default
title: Probability
parent: Curriculum
nav_order: 1
---
### External Resources
- Predrag Radijovac and Marth White's [_Machine Learning Handbook_](https://marthawhite.github.io/mlcourse/notes.pdf)\
Much of this page was directly patterned after sections 1.1-1.4 of this book, which was used to teach this course in a previous semester. 

# Probability
## Part 1: Fundamentals
### Samples and Events
Probability deals with _outcomes_, the results that can and do happen in our world. We'll give some formal definitions to begin with, then flesh them out with a real-world example.

#### Definitions
Formally, we refer to tiny discrete outcomes as **samples**.  We refer to collections of those samples as **events**. Samples are drawn from the set of all samples, the **sample space Ω**; events are drawn from the set of all events, the **event space ℰ**, and (for finite sample spaces) events are just collections of outcomes, ℰ = set of all possible sets of samples, 𝒫(Ω), the power set of Ω.

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

If we consider the outcomes of our lights going out, we have a sample space Ω=`{B R A U M S}`, with each letter corresponding to the light going out. Our events would then be which collection of lights go out - naturally, for example, if we have the event A=`{R A U M S}`, we just have 'B Ice Cream and Dairy Store'. There are certain events we naturally want to avoid - for example, the event A=`{B A M S} = {R U M}ᶜ` - the event where the letters B, A, M, and S go out, or the *complement* of the event where R, U, and M go out - would just leave us with 'RUM Ice Cream and Dairy Store'. A similar unfortunate event is given below.

![Neon "Braum's Ice Cream" sign. The letters B R and A are lit up](braums_incorrect.jpg "Lit-up Braum's Ice Cream Sign fail"){:height="200px" width="200px"}

Exercise: briefly think through what the sample space/event space would be for the lights of a a Snap Fitness™ location (and what events you might want to avoid if you were responsible for it).

![Neon "Snap Fitness" sign. The letters N A and P are lit up, followed by "Fitness"](nap_fitness.png "Lit-up Snap Fitness Sign fail"){:height="200px" width="200px"}

### Probability Distributions
Another example of having an event space is that it allows us to derive probabity distributions. A **probability distribution** is, formally, a function P:ℰ⟶\[0, 1\] from events to the range 0-1 inclusive if
* <img src="https://i.upmath.me/svg/P(%5COmega)%3D1" alt="P(\Omega)=1" /> (the probability of any of the samples occurring is 1)
* <img src="https://i.upmath.me/svg/%5Cforall%20A_1%2C%20A_2%5Cin%20%5Cmathcal%20E%2C%20(A_1%5Ccap%20A_2%20%3D%20%5Cemptyset)%20%5CRightarrow%20P(A_1%20%5Ccup%20A_2)%20%3D%20P(A_1)%20%2B%20P(A_2)" alt="\forall A_1, A_2\in \mathcal E, (A_1\cap A_2 = \emptyset) \Rightarrow P(A_1 \cup A_2) = P(A_1) + P(A_2)" /> (for two disjoint events, the probability that any of their aggregate samples occur (the probability either event occurs) is the same as the sum of the probabilities of the two events)

#### Discrete Example
Consider modelling the probabilities of the roll of a die. The sample space is the finite set Ω = `{1, 2, 3, 4, 5, 6}` and the event space ℰ is the power set P(Ω) = `{∅, {1}, {2}, . . . , {2, 3, 4, 5, 6}, Ω}`, which consists of all possible subsets of Ω. A natural probability distribution on (Ω, E) gives each die roll a 1/6 chance of occurring, defined as P({x}) = 1/6 for x ∈ Ω, P({1, 2}) = 1/3 and so on.¹

The first property just tells us that the event "the die roll is 1, 2, 3, 4, 5, or 6" is 100% likely to happen.
For the second property, consider the event "the die roll is 2 or less" -  A₁=`{1, 2}` - and the event "the die roll is 5 or more" - A₂=`{5, 6}`. The second property tells us that, since A₁ ∩ A₂ = `{}`, P(A₁) + P(A₂) = P(A₁ ∪ A₂). **In other words, the second property tells us that P("getting a die roll ≤ 2 or a die roll ≥ 5") = P("getting a die roll ≤ 2") + P("getting a die roll ≥ 5")**.

These properties can be readily used to derive other facts about probability distributions as well - such as that P(Aᶜ) = 1-P(A).

#### Continuous Example
Consider modelling the probabilities of the angle of a dart thrown against a dartboard. The sample space is the continuous interval Ω = [0, 360] (which is an infinite set). The event space for continuous sets is more complicated than what we've discussed (it's not simply the power set of Ω - it's a subset of that), but for this example, it's the collections of continuous intervals you can form of angles on a dartboard - so, for example, A=`[0, 90]`∈ℰ would be a quarter of the dartboard, as would A=`[330, 60]`∈ℰ.

![Dartboard with some angles highlighted. Specifically, dartboards are split up into radial pieces, and the highest-scoring radial piece extends from the center to the top of the board, bordered by lines along the angles 261 degrees and 279 degrees (the 18 degree sector centered on the line extending from the center to the top of the board)](dartboard.png "Dartboard picture"){:height="200px" width="200px"}

You might imagine that a really good player (who didn't aim for the center) would have a probability distribution that had higher values for intervals between 261 degrees and 279 degrees. Unlike in the discrete case, deriving a probability distribution _P_ here is tricky, as we  Naturally, describing this probability distribution might be a bit tricky- we have have to define outputs for the intervals in the sample space! -  thankfully, as we shall see, we don't need to focus overmuch on the formal definition of a probability distribution to effectively define one.


### Probability Mass & Density Functions
Probability distributions themselves are a bit daunting to consider directly - it can be useful to be able to fall back on their technical sense, but that same  sense is unwieldy to work with. **Fortunately, we can instead obtain probability distributions by simply defining them in terms of _probability density functions_ and _probability mass functions_**.

Probability mass/density functions rely on defining a density value at each point in the sample space - probabilities of items in the event space are then the sum/integral of their constituent samples. It's worth noting that PMFs and PDFs don't necessarily produce probabilities - they can produce values >1, for example.


#### Probability Mass Functions
For a discrete sample space Ω, a PMF is a function <img src="https://i.upmath.me/svg/p%3A%5COmega%20%5Cto%20%5B0%2C%201%5D" alt="p:\Omega \to [0, 1]" /> that satisfies

<img src="https://i.upmath.me/svg/%5Cdisplaystyle%5Csum_%7B%5Comega%5Cin%20%5COmega%7D%7Bp(%5Comega)%7D%3D1" alt="\displaystyle\sum_{\omega\in \Omega}{p(\omega)}=1" />

#### PMF Example
Consider our six-sided die from earlier, where the sample space is Ω = `{1, 2, 3, 4, 5, 6}`. We could have many underlying distributions, but assuming a fair die (a.k.a. unweighted) we have

<img src="https://i.upmath.me/svg/p(%5Comega)%20%3D%20%5Cfrac%7B1%7D%7B6%7D" alt="p(\omega) = \frac{1}{6}" />

Using, this, if we wanted to find the probability of rolling an odd number, we could do P({1, 6}) = p(1) + p(6) = 1/6 + 1/6 = 2/3.

This generalizes to more complicated s - in the eveutations in the event there was some more complicated underlying distribution, like if someone was cheating with a weighted die, we could also use a PMF to model that.

#### Probability Density Functions
For a continuous sample space Ω, a PMF is a function <img src="https://i.upmath.me/svg/p%3A%5COmega%20%5Cto%20%5B0%2C%201%5D" alt="p:\Omega \to [0, 1]" /> that satisfies

<img src="https://i.upmath.me/svg/%5Cdisplaystyle%5Cint_%7B%5Comega%5Cin%20%5COmega%7D%7Bp(%5Comega)%7D%3D1" alt="\displaystyle\int_{\omega\in \Omega}{p(\omega)}=1" />

### Expected Values
### Independence and Effective Independence
### Product Rule and Bayes's Theorem
## Part 2: Applications


¹ Text taken nearly directly from Predrag Radijovac and Marth White's _Machine Learning Handbook_ at https://marthawhite.github.io/mlcourse/notes.pdf
