---
layout: post
author: jesse
title: Laplace's rule of succession
header-includes: \mid 
    \usepackage{mymacros}
---

# Laplace's rule of succession

Consider an urn with $N$ balls from which $R$ are red and $N-R$ are black. We now draw $n$ balls without replacement and find that $r$ balls are red. We denote this data by $D=(n,r)$. Suppose we know $N$ but don't know $R$. We ask ourselves the following two questions: 
1. What is the expected fraction of red balls left after observing $D$?
2. What is the probability of drawing a red ball on the $(n+1)$th draw after observing $D$?

Our initial background information is given by $I$. Part of this is a uniform prior over $R$,

$$p(R|NI) = \frac{1}{N+1} \ \ \  0 \leq R \leq N$$

### Question 1
We start with the first question. The expected fraction can be written as follows:

$$ \bE\left[\frac{R-r}{N-n} \mid NDI\right] = \frac{\bE[R \mid NI] - r}{N-n}  $$

The expectation of $R$ is given by (see appendix for details)
$$ \bE[R \mid DNI] = \frac{(N+2)(r+1)}{(n+2)} - 1$$

Combining the above two equation and working out gives

$$ \bE\left[\frac{R-r}{N-n} \mid NDI\right] = \frac{r+1}{n+2} $$

### Question 2

We call $R_{n+1}$ the event "red at $(n+1)$th draw". We want to compute

$$ p(R_{n+1}\mid DNI) $$

We can compute this by conditioning on $R$. 

$$ p(R_{n+1}\mid DNI) = \sum_{R=0}^N p(R_{n+1}\mid RDNI) p(R \mid DNI) $$

Working this out (see appendix) gives

$$ p(R_{n+1}\mid DNI) = \frac{r+1}{n+2} $$

### Interpretation

Note that Laplace's rule of succession can be written in the form

$$\frac{r+1}{n+2} = \frac{n(r/n) + 2(1/2)}{n+2}. $$

Note that this can be interpreted as a weighted average of the observation $r/n$ and the prior expectation $1/2$. The data is weighted by $n$ and the prior expectations by $2$. This raises the question, can the prior be interpreted as a posterior distribution resulting from two observations $(n,r) = (2,1)$. The below figure displays how the prior information is pushing the posterior closer to $1/2$. 

<img src="/assets/images/graph-r-n.png" width="500">


## Appendix


The posterior of $R$ can be computed using Bayes' rule.
$$ p(R \mid DNI) = p(R | NI) \frac{p(D|RNI)}{p(D|NI)}$$
$$ = \binom{N+1}{n+1}^{-1} \binom{R}{r}\binom{N-R}{n-r}, $$

where we use

$$\sum_{R=0}^N \binom{R}{r}\binom{N-R}{n-r} = \binom{N+1}{n+1}.$$


