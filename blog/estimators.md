---
layout: post
author: jesse
title: Estimators
header-includes: \mid 
    \usepackage{mymacros}
---

# Estimators

### Question

Let $a_1, ..., a_n \in \bR$ and let $\bar{a}$ be the average of $\{a_1, ..., a_n\}$, i.e. $\bar{a} = \frac{1}{n} \sum_i a_i$. Which of the following statements is true:

1. $\bar{a} = \argmin_{a'\in \bR} \sum_i a_i - a'$ 
2. $\bar{a} = \argmin_{a'\in \bR} \sum_i (a_i - a')^2$ 

---

## Summarizing a (probability) distribution

We often want to summarize a distribution with one number. For example, the grades of a student, the incomes of citizen in a country, our beliefs about a certain unknown parameter. In statistics, this number is called an estimator. In this post we discuss some considerations for choosing an estimator. 

### Different objectives

One possible objective for an estimator $a^*$ is to minimize the expected distance from a sample from the distribution. 

$$a^*_{(1)} =  \argmin_{a'\in \bR} \int |x - a'| p(x) dx$$

It turns out that this objective leads to $a^*_{(1)}$ such that 

$$ \int_{-\infty}^{a^*_{(1)}} p(x) dx = \int^{\infty}_{a^*_{(1)}} p(x) dx,$$

which is the median. 

Another objective is the following:

$$a^*_{(2)} =  \argmin_{a'\in \bR} \int (x - a')^2 p(x) dx,$$

which leads to the average, or expected value, of the distribution. I.e.

$$ a^*_{(2)}  = \bE_{p(x)}(x) = \int x p(x) dx. $$

The last objective we discuss is the following:

$$ a^*_{(3)} = \argmax_{a'\in \bR} p(a').  $$

Which is called the mode. In the context of parameter estimation, where the distribution is a posterior distribution, this estimator is called the maximum a posteriori probability (MAP) estimator.  

### Estimators in practice


#### binomial 
Suppose I have a coin which lands heads 90% of the time. If I throw this coin $1 * 10^{12}$ times, what would be your guess how often it lands up heads?

If your guess is $0.9 * 10^{12}$, you would be optimizing Objective 1 and 3, but actually not Objective 2. Objective 2 is optimized for $a^* = 900000000004$. 

In case we throw $9$ times, the maximum of $p(x)$ lies both at $x = 8$ and $x = 9$.
Therefore the mode is not unique. The expected value is $8.1$. 

#### distribution for which mode and average are more clearly different

#### why is average more natural when choosing an estimator for forward probability, and mode for parameter estimation (MLE)


## Appendix

#### answer to question 
The truth of Statement 2 can easily be proven by taking the derivate of sum w.r.t. $a'$ and setting it to zero. The average can therefore also be seen as the 
$L^2$ 
projection of a sequence on the space of constant sequences. 

#### derivation of median

#### show that average and mode for binomial are equal