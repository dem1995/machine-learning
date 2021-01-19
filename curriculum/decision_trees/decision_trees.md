---
layout: default
title: Decision Trees
parent: Curriculum
nav_order: 2
---
### External Resources
- (Before/During) [Prateek Karkare's _Decision Trees — An Intuitive Introduction_](https://www.kdnuggets.com/2019/02/decision-trees-introduction.html) offers a very good first glance at decision trees. I highly recommend checking it out, especially the first page. You can look at it before reading this page without issue.
- (During/After) [Kilian Weinberger's SVM Lecture Notes](https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote09.html) Interactive demo for plotting points/forming a decision tree for classified points in a 2D plane. Also useful for understanding decision trees in the sense of a spatial perspective upon the data being classified, and has pseudocode for training a decision tree.

# Decision Trees
## Introduction - "What is a a decision tree?"
Every day you make decisions. What food to get from the grocery store, what to prepare for dinner that night, who to hang out with after after work (and where, when we're not in the middle of a pandemic). Some of these decisions are simple - but for the more complicated ones, how do you break it down? One way of doing so is by breaking a larger decision into a bunch of smaller decisions.

A **decision tree** is a tree used for classifying outcomes - given some set of information, you answer some question by proceeding down the tree, answering smaller questions to guide you along the way.

### Example of a tree
![Decision tree for getting an apartment](apartment_decision_tree.png)

Above, for example, is a (simplified) example of a decision tree for me choosing an apartment. If you select a given apartment, you can follow the tree to determine whether I would classify it as an "apartment I want" or "an apartment I don't want". Notice that at the beginning of the tree all apartments are feasible - of

### Properties/Terminology
Recall some terminology/properties about trees: the head of a tree is called the "root", the bottoms of the tree are called "leaf nodes/terminal nodes", and the connections between arbitrary nodes in the tree are called "edges". Trees, by definition, only ever proceed from roots to leaf nodes - you don't have any child nodes that have multiple parents, and you don't end up with cycles anywhere in the tree. **In the case of a decision tree, the leaves are outcomes, and the edges are decisions**. 

Despite the fact that you'll commonly see decision trees that are binary - that is, trees where every nonterminal node has two children; trees where every node has exactly two possible decisions - decision trees can have as many branches as you want. As an example, consider trying to decide whether a day is "rainy" based on month of the year - the node might break into Late Winter, Spring, Summer, Fall, and Early Winter nodes.


### Probability
## Intuition - partitioning space
### Curse of Dimensionality
## Forests
### Voting
## Random Forest Classifiers
