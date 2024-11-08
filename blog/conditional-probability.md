---
layout: post
---

# Conditional probability

A _Markov kernel_ from $(X, \mathcal{X})$ to $(Y, \mathcal{Y})$ is a map $K: X \times \mathcal{Y} \rightarrow [0, 1]$ that satisfies the following properties:

1.For every $B \in \mathcal{Y}$, the map $x \mapsto K(x, B)$ is $\mathcal{X}$-measurable.  
2.For each $x \in X$, the set function $K(x, \cdot)$ is a probability measure on $(Y, \mathcal{Y})$.

Let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, and let $\mathcal{G} \subset \mathcal{F}$ be a sub-$\sigma$-algebra of $\mathcal{F}$. Given a random variable $Y$ taking values in a measurable space $(S, \mathcal{S})$, a **regular version of the conditional probability** of $Y$ given $\mathcal{G}$ is a Markov kernel $K: \Omega \times \mathcal{S} \rightarrow [0, 1]$ satisfying:

1. **Probability Measure Property**: For each $\omega \in \Omega$, the function $K(\omega, \cdot)$ is a probability measure on $(S, \mathcal{S})$.
2. **Measurability**: For each $B \in \mathcal{S}$, the map $\omega \mapsto K(\omega, B)$ is $\mathcal{G}$-measurable.
3. **Conditioning Consistency**: For any $B \in \mathcal{S}$ and $G \in \mathcal{G}$,
   $$
   \mathbb{E}[\mathbf{1}_{\{Y \in B\}} \mid \mathcal{G}](\omega) = K(\omega, B) \quad \text{almost surely on } G.
   $$
   This means that $K(\omega, B)$ behaves like a "conditional probability distribution" of $Y$ given the information contained in $\mathcal{G}$.


Let $X$ be a random variable on the probability space $(\Omega, \Sigma, \bP)$. For any sub sigma algebra $\cF \sub \Sigma$ we can define a version of the *conditional expectation* $\bE[X \vert \cF]$ which is a $\cF$-measureable function such that for all $A \in \cF$ we have 

$$ \int_A X d\bP = \int_A \bE[X \vert \cF] d\bP. $$

To prove existence we can define the measure on $\cF$

$$\bQ(A) = \int_A X d\bP.$$

It can be shown that the a version of the conditional expectaton is given by the Radon Nykodym derivative $$\frac{d\bQ}{d\bP}$$. 

A version of the *conditional probability* is defined by 

$$P(A \vert \cF) = \bE[\mathbb{1}_A \vert \cF]$$

It turns out that the conditional probability constructed in this way does not always satisfy 


## outline 

definitie markov kernel, regular version conditional probability, given Y=y, in terms of joint distribution. (posterior distribution). First condition can always be satisfied by choosing the posterior to be a version of the conditional probability (conditional expectation). The second condition is only satisfied when extra conditions are assumed. 

