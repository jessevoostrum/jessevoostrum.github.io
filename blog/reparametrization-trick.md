---
layout: post
author: jesse
title: Reparametrization Trick
---

# Reparameterization Trick 

### Naive Monte Carlo Gradient Estimation
When we want to estimate the gradient of an expectation, say $$ \mathbb{E}_{x \sim p(x \vert \theta)}[f(x)] $$, with respect to the parameters $$\theta$$, the naive approach is to compute:

$$\nabla_{\theta} \mathbb{E}_{x \sim p(x\vert\theta)}[f(x)] = \mathbb{E}_{x \sim p(x\vert\theta)}[f(x) \nabla_{\theta} \log p(x\vert\theta)]$$

This is typically estimated by sampling:

$$\frac{1}{N} \sum_{i=1}^N f(x_i) \nabla_{\theta} \log p(x_i\vert\theta)$$

where $$ x_i $$ are drawn from the distribution $$ p(x \vert \theta) $$.

### Reparameterization Trick
Alternatively we can sample $\epsilon$ from a fixed distribution $q$. Then we use a deterministic function $g$ such that 

$$ g(\epsilon, \theta) \sim p(x \vert \theta). $$

We can now rewrite the gradient of the expectation as follows

$$ 
\begin{align}
    \nabla_{\theta} \mathbb{E}_{x \sim p(x \vert \theta)}[f(x)] &= \nabla_{\theta} \mathbb{E}_{\epsilon \sim q}[f(g(\epsilon, \theta))]\\
    &=  \mathbb{E}_{\epsilon \sim q}[ \nabla_{\theta} f(g(\epsilon, \theta))]\\
    &=  \mathbb{E}_{\epsilon \sim q} \left[
        \frac{\partial f}{\partial x} (g(\epsilon, \theta) ) \nabla_{\theta} g(\epsilon, \theta) 
     \right]
\end{align}
$$

### Example: Gaussian Distribution

#### Scenario
Suppose we have a simple probabilistic model where we want to optimize the expectation of a function $$ f(x) $$ under a Gaussian distribution $$ x \sim \mathcal{N}(\mu, \sigma^2) $$ with respect to the mean $$ \mu $$. The objective is:

$$\mathbb{E}_{x \sim \mathcal{N}(\mu, \sigma^2)}[f(x)]$$

We want to compute the gradient of this expectation with respect to the parameter $$\mu$$.

#### Naive Monte Carlo Gradient Estimation
Using the score function (REINFORCE) method, the gradient is given by:

$$\nabla_{\mu} \mathbb{E}_{x \sim \mathcal{N}(\mu, \sigma^2)}[f(x)] = \mathbb{E}_{x \sim \mathcal{N}(\mu, \sigma^2)}[f(x) \nabla_{\mu} \log p(x\vert\mu, \sigma)]$$

For a Gaussian distribution, the log-probability $$ \log p(x\vert\mu, \sigma) $$ is:

$$\log p(x\vert\mu, \sigma) = -\frac{(x - \mu)^2}{2\sigma^2} - \log(\sigma\sqrt{2\pi})$$

The gradient with respect to $$\mu$$ is:

$$\nabla_{\mu} \log p(x\vert\mu, \sigma) = \frac{x - \mu}{\sigma^2}$$

Thus, the naive Monte Carlo estimate of the gradient is:

$$\frac{1}{N} \sum_{i=1}^N f(x_i) \frac{x_i - \mu}{\sigma^2}$$

where $$ x_i \sim \mathcal{N}(\mu, \sigma^2) $$.

**Issue**: This estimate can have high variance, especially if $$ f(x) $$ is non-linear or has large variations. The term $$ f(x_i) \frac{x_i - \mu}{\sigma^2} $$ can fluctuate significantly, leading to high variance in the gradient estimate.

#### Reparameterization Trick
The reparameterization trick allows us to rewrite the random variable $$ x $$ in a way that separates the randomness from the parameters. For a Gaussian distribution, we can express $$ x $$ as:

$$x = \mu + \sigma \cdot \epsilon = g(\epsilon, \theta)$$

where $$ \epsilon \sim \mathcal{N}(0, 1) = q $$ is a standard normal random variable.

The expectation can now be written as:

$$\mathbb{E}_{x \sim \mathcal{N}(\mu, \sigma^2)}[f(x)] = \mathbb{E}_{\epsilon \sim \mathcal{N}(0, 1)}[f(\mu + \sigma \cdot \epsilon)]$$

The gradient with respect to $$ \mu $$ is:

$$\nabla_{\mu} \mathbb{E}_{\epsilon \sim \mathcal{N}(0, 1)}[f(\mu + \sigma \cdot \epsilon)] = \mathbb{E}_{\epsilon \sim \mathcal{N}(0, 1)}[\nabla_{\mu} f(\mu + \sigma \cdot \epsilon)]$$

Since $$ \mu $$ appears directly inside $$ f(\mu + \sigma \cdot \epsilon) $$, the gradient is:

$$\mathbb{E}_{\epsilon \sim \mathcal{N}(0, 1)}\left[\frac{\partial f(\mu + \sigma \cdot \epsilon)}{\partial \mu} \right] = \mathbb{E}_{\epsilon \sim \mathcal{N}(0, 1)}\left[\frac{\partial f}{\partial x} (\mu + \sigma \cdot \epsilon)\right]$$

In practice, this is estimated using:

$$\frac{1}{N} \sum_{i=1}^N \frac{\partial f}{\partial x} (\mu + \sigma \cdot \epsilon_i)$$

where $$ \epsilon_i \sim \mathcal{N}(0, 1) $$.

**Benefit**: This method typically results in lower variance because the gradient $$ \frac{\partial f}{\partial x} (\mu + \sigma \cdot \epsilon)$$ is computed directly, which often captures the underlying smoothness or structure of $$ f(x) $$ better than the product of $$ f(x) $$ and the score function $$ \frac{x - \mu}{\sigma^2} $$.

