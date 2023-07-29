---
layout: post
author: jesse
title: Perception according to the Free energy principle
header-includes: |
    \usepackage{mymacros}
---

# Perception according to the Free energy principle

Perception consists of two parts 
1. learning a generative model of the world 
2. performing inference on this model 

## Learning 
In order to learn the the generative model $p_\theta(x,z)$, the Free energy principle suggest to maximize the evidence of an observation $x$ using gradient ascent. The evidence is given by $\ln p_\theta(x)$. The gradient of the evidence w.r.t. $\theta$ is given by
$$\frac{\partial}{\partial\theta} p_\theta(x) = \sum_z p_\theta(z|x) \frac{\partial}{\partial\theta}\ln p_\theta(x,z).$$
Note that in order to compute this gradient we need to have access to $p_\theta(z|x)$. In the next section we discuss how this can be approximated. 


## Inference

Assume that we have a model  $p_\theta(x | z)$  of how the world is generating observations $x$ from latent causes $z$, and we have a prior distribution $p_\theta(z)$ over latent causes. Given a specific observation $x$, the goal of inference is to find the posterior distribution $p_\theta(x | z)$. Computing this distribution exactly is often hard. The Free energy principle suggest to find an approximate posterior $q_x(z)$ in a family of distributions $\cQ$ that minimises the following free energy function w.r.t. $q$:
$$\cF(p,q,x) = \sum_z q(z) \ln\frac{q(z)}{p_\theta(x,z)}.$$
Thus,
$$q_x(z) = \argmin_{q \in \cQ} \cF(p,q,x).$$ 
Note that when $\cQ$ is the set of all distributions over $z$, $q_x(z)$ will simply be equal to $p_\theta(z|x)$. Usually, however, $\cQ$ is does not contain all probability distributions, and is paramtrized by a parameter $\phi$. 