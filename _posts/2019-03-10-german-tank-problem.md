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
These tanks were built out of parts with imprinted serial numbers in an ascending sequence, thus, when a tank has been distroyed, Allied forces gained access to these serial numbers.\\
With this information statisticians have been able to estimate how many tanks were produced.

## Problem definition

Assuming we have a population of unknown size $N$, which is labeled using serial number $(1,\cdots,N)$ and we found out $k\leq N$ tanks $X = (X_1,\cdots,X_k)$, where the number $X_i$ corresponds to the serial number of the $i^{th}$ tank.\\
How could we make an inference of $N$ through the observations $X$?\\
The probability mass function is:

$$P_N(x)={\begin{cases}{\frac {1}{N}}&\mathrm {for} \ x\leq N,\\[8pt]0&\mathrm {otherwise}\end{cases}}$$

thus the likelihood function for the sample of $k$ tanks (assuming they are an independent random sample, which is a not trivial assumption since in a sampling without remplacement observations are not independent but if we suppose $N\gg k $ the error introduced by assuming the independence is not large) is the following:

$$\mathcal {L} (N; x_1, \cdots,x_k) ={\begin{cases}{\frac {1}{N^k}}&\mathrm {for} \ \mathrm {max} (x_i)\leq N,\\[8pt]0&\mathrm {otherwise} \end{cases}}$$

More observation we have the better will be the estimate, where the maximum likelihood estimator of $N$ is $M = \mathrm {max} (x_1, \cdots,x_k)$, the largest serial number. The likelihood function looks like the below when 10 tanks have been knocked out (getting more evidence, we update our beliefs):\\

<img src="../figures/Frequentist German Tank Problem/Int_1.PNG" style="width: 100px ;margin-right: 5px" img align="left" />
<img src="../figures/Frequentist German Tank Problem/Int_2.PNG" style="width: 100px;margin-right: 5px" img align="right" />

Intuitively $M$ is a bad estimator because it will underestimate $N$ on average. To compute the bias we have to derive the expectation of $M$, so let's start by finding out the CDF of $M$, for $x \geq k$ it is:

$$\begin{align} F_M(x) &= \Prb(X_1 \leq x,\cdots, X_k \leq x) \\ &= \Prb(X_1 \leq x)\Prb(X_2 \leq x | X_1 \leq x)\ldots  \Prb(X_k \leq x | X_i \leq x \, \forall i = 1, \cdots, k - 1) \\ &= \frac {x}{N}\cdots \frac {x-k+1}{N-k+1} = \frac {\binom{x}{k}}{\binom{N}{k}}  \end{align} $$


Then the probability mass function is:

$$\begin{align} \Prb(M = x) &= F_M(x) - F_M(x-1) \\ &= \frac {\binom{x}{k}}{\binom{N}{k}} - \frac {\binom{x-1}{k}}{\binom{N}{k}}   = \frac {\binom{x-1}{k-1}}{\binom{N}{k}}\end{align}. $$

To notice that from this last expression we can derive the hockey-stick identity:

$$ \sum_{x = k}^N \Prb(M = x) = 1 = \frac {\sum_{x = k}^N \binom{x-1}{k-1}}{\binom{N}{k}}$$

So the following holds

$$\sum_{x = k}^N \binom{x-1}{k-1} = \binom{N}{k} $$

Now we have the elements to compute the expectation: 
$$ \begin{align} \Expect[M] = \frac {\sum_{x = k}^N x\binom{x-1}{k-1}}{\binom{N}{k}} = \frac {\sum_{x = k}^N k\binom{x}{k}}{\binom{N}{k}} = k\frac{\binom{N+1}{k+1}}{\binom{N}{k}} = k\frac {N+1}{k+1} \end{align}. $$

  The bias of this estimate is $(k-N)/(k+1)$, so only observing the entirety of production we can guarantee an unbiased estimate. In order to correct the bias we can rewrite the last expression to obtain:
  
$$\hat{N} = M\frac{k+1}{k}-1$$





