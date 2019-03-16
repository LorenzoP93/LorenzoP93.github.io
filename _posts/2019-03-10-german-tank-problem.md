---
layout: post
title: "Frequentist German Tank Problem"
description:
date: 2019-03-10
tags: estimation
comments: true
---

$$
  \newcommand{\R}{\mathbb{R}}
  \newcommand{\Prb}{\mathbb{P}}
  \newcommand{\Expect}{\mathrm{E}}
  \newcommand{\Var}{\mathrm{Var}}
  \newcommand{\Cov}{\mathrm{Cov}}
  \newcommand{\indep}{\rotatebox[origin=c]{90}{$\models$}}
  \newcommand{\argmin}[1]{\underset{#1}{\mathrm{arg min}}\;}
  \newcommand{\argmax}[1]{\underset{#1}{\mathrm{arg max}}\;}
  \newcommand{\norm}[1]{\left\lVert#1\right\rVert}
  \newcommand{\diff}{\mathrm{d}}
  \DeclareMathOperator{\Tr}{Tr}
  \let\emptyset\varnothing
$$

## Introduction

During World War II Allied forces tried to defeat Germany and in order to do so any information was used. Surely having a clear view on the German production of tanks could make a great difference to balance a counter strategy.\\
These tanks were built out of parts with imprinted serial numbers in an ascending sequence, thus, when a tank has been distroyed Allied forces gained access to these serial numbers.\\
With this information statisticians have been able to estimate how many tanks were produced.

## Problem definition

Assuming we have a population of unknown size $N$, which is labeled using serial number ${1,\cdots,N}$ and a random sample $X = (X_1,\cdots,X_k)$ of size $k\leq N$ is observed.\\
How could we make an inference of $N$ through the observations $X$?
So we found out $k$ tanks where the number $X_i$ corresponds to the serial number of the $i^{th}$ tank.\\
The probability mass function is:

f_N(x)={\begin{cases}{\frac {1}{N}}&\mathrm {for} \ x\leq N,\\[8pt]0&\mathrm {for} \ x>N\end{cases}}



