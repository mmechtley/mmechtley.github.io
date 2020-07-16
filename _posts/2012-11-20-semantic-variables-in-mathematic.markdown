---
layout: post
title: Semantic Variables in Mathematics
date: 2012-11-20 00:37:00 -0700
categories: math programming
---

I think a lot about how to teach people programming and mathematics. Particularly since beginning to use Python a couple years ago, I have focused a lot on teaching people to produce readable code.

A perennially confusing topic when teaching programming is the variables `i` and `j` commonly used in 2D iteration. Without fail, you will one day be working [at 3am/in a new language/drunk] and forget which of these is the row of your matrix and which is the column. There is a very simple solution to this problem, which I stress to anyone I teach: **_Always_ use semantic names for your variables.** I have doubly stressed the word always because _I mean it_. In the case of matrices, the variable names `row` and `col` are still pretty short but communicate infinitely more information. I no longer even use `i` when doing simple loops, instead preferring semantic names like `step`. This is good practice for anyone, but isn't a new idea when writing code.

A couple days ago, I was helping my partner learn how to program partial differential equations using the [finite difference method](http://en.wikipedia.org/wiki/Finite_difference_method). We were working on the canonical example of the 2D time-dependent heat equation:

$$\frac{\partial^2 h}{\partial x^2} + \frac{\partial^2 h}{\partial y^2} = \frac{\partial h}{\partial t}$$

To discretize this equation, you usually split up your x,y plane into a matrix of points separated by some step size, Δx. You then consider the amount of heat at one point i,j at time n, and how it evolves to time n+1. The usual notation is something like this (assuming that the step size in x and y is the same):

$$\frac{h_{i-1,j}^{n} + h_{i+1,j}^{n} + h_{i,j-1}^{n} + h_{i,j+1}^{n} - 4h_{i,j}^{n}}{\Delta x^2} = \frac{h_{i,j}^{n+1} - h_{i,j}^{n}}{\Delta t}$$

Horrifying! Here are all these i's and j's again. What is their semantic meaning? A careful reading will show that they are referring to contributions from the neighboring points in our gridded domain. The i,j tuple here in fact refers to a single point, just in two dimensions, and the +/-1 refers to its neighbor in each direction. Suppose we applied the semantic naming idea here, and didn't limit ourselves to only letters:

$$\frac{h_{p \leftarrow}^{now} + h_{p \rightarrow}^{now} + h_{p \uparrow}^{now} + h_{p \downarrow}^{now} - 4h_{p}^{now}}{\Delta x^2} = \frac{h_{p}^{next} - h_{p}^{now}}{\Delta t}$$

I think this goes a long way toward better communicating what is actually going on in the discretization equation. The symbols now help us instead of confuse us, because they carry semantic meaning. We are used to understanding p to mean a point in space (and we could even call it pt), and the arrows symbolically indicate that we're looking at neighbors. It's about as compact as the original when written by hand, and only slightly longer when marked up in LaTeX. You do still have to explain the notation, but that was also true of i,j, and n — they just didn't carry any semantic meaning to help you remember their purpose.
