---
layout: post
author: jesse
title: Notation in probability theory
header-includes: |
    \usepackage{mymacros}
---

# Notation in probability theory 

Bad choice of notation can lead to ambiguities and therefore potential failure of conveying your ideas clearly to other people. In this post, I discuss some notational issues related to probability theory. 

## Background

Formally the setting in probability theory is as follows. One has a set $\Omega$ called a _sample space_ together with a set $\Sigma$ containing subsets of $\Omega$ called a $\sigma$-_algebra_. Together $(\Omega, \Sigma)$ are called a _measurable space_. Now we can introduce a _measure_ $\mu$ on $(\Omega, \Sigma)$, which is a map from $\Sigma$ to $\bR_{\geq 0}$. The triple $(\Omega, \Sigma, \mu)$ is called a _measure space_. When $\mu$ satisfies the additional property that $\mu(\Omega) = 1$, $\mu$ is called a _probability measure_, and $(\Omega, \Sigma, \mu)$ is called a probability space, which we fix to be the case. A _random variable_ $X$ is a map from $\Omega$ to $\sS$, where $\sS$ is either finite, in which case $X$ is called _discrete_, or $\sS = \bR^n$, in which case $X$ is called _continuous_. $\sS$ can be equipped with its own $\sigma$-algebra $\cS$ such that $(\sS, \cS)$ becomes a measurable space. The _distribution_ $P$ of $X$ is a measure on $(\sS, \cS)$ such that for $A \in \cS$, $P(A) = \mu(X^{-1}(A))$, i.e. $P$ is the _pushforward measure_ of $\mu$ through $X$. For discrete $X$, the _probability mass function_ $p$ is a function from $\sS$ to $[0,1]$ such that for any subset $S \in \cS$
$$P(S) = \sum_{x\in S} p(x)$$ 
For continuous $X$, the _density function_ $p$ of $X$ is a function from $\bR^n$ to $\bR$ such that for any open subset $S \subset \bR^n$ we have
$$P(S) = \int_S p(x) dx.$$  


## Considerations when choosing notation

In practice, the underlying probability space $(\Omega, \Sigma, \mu)$ is often ignored, and we work only in the image space $\sS$ of the random variable, e.g. in $\bR$. 

### Distribution $P$ vs density $p$ 
Although these two concept are different, they are often used interchangeably. A distribution takes as argument a <u>subset</u> of the image space of $X$, e.g. an interval $(a,b) \subset \bR$. A density function takes as argument an <u>element</u> of the image space of the random variable, e.g. $3.412  \in \bR$. In case $X$ is discrete the difference between the two becomes less important, since elements $x \in \sS$ correspond directly to subsets $\{x\} \subset \sS$.  

### Using the same $p$ for different distributions / densities
As we have seen in the Background section, every distribution or density belongs to a specific random variable. Since $p$ is such a common letter for a probability distribution / density, it is often used as the symbol for multiple random variables. While in many cases this is possible, since we can still precise what is meant by specifying the variable: e.g. $p(x)$ for $X$ and $p(y)$ for $Y$, it can also sometimes lead to ambiguities. 

### Distinguishing $\bR^n, n>1$ from $\bR$ 
Many sources emphasize the fact that an element lives in a multidimensional space by using writing $\mathbf{x}$ or $\bar{x}$. The separate elements of the vector are then denoted e.g. $x_i$. However, when the elements have an index, the full vector $x$ can be simply distinguished by having no index. 


## Formal definitions

#### $\sigma$-algebra
A $\sigma$-algebra on $\Omega$ is set of subsets of $\Omega$ that satisfies the following properties: 
- $\Omega \in \Sigma$,
- $A \in \Sigma \implies \Omega \setminus A \in \Sigma$,
- $(A_i)_{i\in\bN} \in \Sigma \implies \bigcap_i A_i \in \Sigma$.

#### measure 
A measure $\mu$ is a map $\mu:\Sigma \to \bR_{\geq0}$ that satisfies the following properties: 
- $\mu(\emptyset) = 0$, 
- For $(A_i)_{i\in\bN} \in \Sigma$ such that $A_k \cap A_l = \emptyset$ for all $k,l \in \bN$, we have 
$$\mu\left(\bigcup_i A_i \right) = \sum_i \mu\left( A_i \right)$$

#### random variable
A function $f: (\sA, \cA) \to (\sB, \cB)$ is called _measurable_ when for all $B \in \cB$ we have $f^{-1}(B) \in \cA$. A random variable is required to be measurable. 

#### mass and density function 
These function can also be defined more generally in terms of the Radom-Nikodym derivative. For a reference measure $\nu$ on $(\sS, \cS)$, which is typically the counting measure for finite $\sS$ and the Lebesgue measure for $\sS = \bR$, the $p$ is defined to be 
$$ p(x) = \frac{dP}{d\nu}(x).$$  


## To add

- conditional probability 