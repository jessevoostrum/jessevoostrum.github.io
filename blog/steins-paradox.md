--- 
layout: post
---

# Stein's Paradox

Consider estimating a vector-valued parameter $\theta \in$ $\mathbb{R}^d$ based on an observation $X$ with the $N_d\left(\theta, \sigma^2 I\right)$-distribution, i.e. the coordinates $X_1, \ldots, X_d$ of $X$ are independent random variables with $X_i \sim N\left(\theta_i, \sigma^2\right)$. There are no known relationships between the coordinates $\theta_1, \ldots, \theta_d$ of $\theta$, and we consider $\sigma^2$ to be known.

The maximum likelihood estimator of $\theta$ is the vector $X$ itself and has mean square error $\mathrm{E}_\theta\|X-\theta\|^2=d \sigma^2$. Somewhat surprisingly, for $d \geq 3$ there exist estimators with a smaller mean square error, and even much smaller if $d$ is big.

## Intuition

My friend Peter came up with the following intuition. Let $X_1, \ldots, X_d$ be our sample, or vector in $\bR^n$. Hypothetically, we can apply a coordinate transformation, so that the true mean lies on the first coordinate axis. In this new coordinate system all other coordinates $\tilde{\theta_2}, ..., \tilde{\theta_d}$ are zero. Shrinking the first coordinate of our transformed vector $\tilde{X_1},...\tilde{X_d}$ will have a negative effect on the accuracy of that coordinate. However, for all the other coordinates it will have a positive effect. It turns out that from $d=3$ this positive effect will outweigh the negative effect on $\tilde{X_1}$. 

In (Szabó, van der Vaart 2023) they write: "That shrinkage is a good idea is also suggested by the fact that $\mathrm{E}_\theta\|X\|^2=\|\theta\|^2+d \sigma^2$ : the vector $X$ is "too big" for estimating the vector $\theta$."