---
layout: post
author: jesse
title: Variational Autoencoder
---

# Variational Autoencoder

The variational autoencoder consists of two parametrized distributions $p_\theta(x,z)$ and $q_\phi(z\vert x)$ called the generative and recognition model respectively. For a specific datum $x^{(i)}$ the learning objective is given by

$$
\begin{align*}
\cL(\theta, \phi, x^{(i)}) &= \bE_{z\sim q_\phi(z\vert x^{(i)})} \left[ - \ln q_\phi(z\vert x^{(i)}) + \ln p_\theta(x^{(i)},z) \right] \\
&= - D(q_\phi(z\vert x^{(i)}) \parallel p_\theta(z)) + \bE_{z\sim q_\phi(z\vert x^{(i)})} \left[  \ln p_\theta(x^{(i)} \vert z) \right]
\end{align*}
$$

The first term is called the _latent loss_ and the second term the _reconstruction error_. In order to minimize this loss we compute the gradient with respect to $\theta$ and $\phi$. As an example we work out this gradient for the the reconstruction loss. 

In order to approximate the expectation we want to make use of sampling. Note however that the distribution of $z$ depends on the parameter $\phi$. There are two ways to circumvent this, discussed in the post [_Reparametrization Trick_](/blog/reparametrization-trick), where the reparametrization trick is favoured and is the one we will use here. We get 

$$
\begin{align*}
    \bE_{z\sim q_\phi(z\vert x^{(i)})} \left[  \ln p_\theta(x^{(i)} \vert z) \right] &\approx \sum_l \ln p_\theta(x^{(i)} \vert g_\phi(\epsilon^{(l)}, x^{(i)}))
\end{align*}
$$

This can now be derived with respect to both $\theta$ and $\phi$. In case $q_\phi$ is a normal distribution the samples $z^{(i,l)}$ are given by 

$$
\begin{align*}
    z^{(i,l)} = g_\phi(\epsilon^{(l)}, x^{(i)}) = \mu(\phi, x^{(i)}) + \sigma(\phi, x^{(i)}) \epsilon^{(l)}
\end{align*}
$$

