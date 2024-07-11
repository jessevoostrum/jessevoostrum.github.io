---
layout: post
author: jesse
title: Bayesian Reasoning
---

# Bayesian Reasoning    

## Interpretations of probability

_interpretation 1 (frequentist):_  
frequencies of outcomes in random experiments

_interpretation 2 (Bayesian)_  
degrees of belief in propositions given the background information  
‘the probability that Mr. S. was the murderer of Mrs. S., given the evidence.’  


## Probability theory as extension of logic

Aristotelian logic deals with propositions that are either true or false with certainty, and derives deductive rules for these. For example 

$$ (A \implies B) \implies (\bar{B} \implies \bar{A}).$$

The following rule however is incorrect:

$$ (A \implies B) \implies (B \implies A).$$

Consider the following example propositions: 

- $A$ = it will start to rain by 10 am at the latest;
- $B$ = the sky will become cloudy before 10 am.

The first (correct) rule says, if it starts to rain at 10, then the sky will have become cloudy before 10. The second (incorrect) rule says, if it is cloudy before 10, then it will rain at 10. Common sense tells us however that observing $B$ does make $A$ more likely. We therefore need a systematic way of dealing with uncertainty, to extend the rules of Aristotelian logic. 

### Notation

Let ‘the degree of belief in proposition $A$, given background information $I$’ be denoted by $\bel(A \mid I)$. The negation of $A$ ($\texttt{NOT}$-$A$) is written $\bar{A}$. And the intersection of $A$ and $B$, ($A$ $\texttt{AND}$ $B$), is written $A,B$ or $AB$. The union of $A$ and $B$, ($A$ $\texttt{OR}$ $B$) is written $A + B$. For ease of notation we sometimes drop the conditioning on the background information $I$. 

### Cox' Axioms

- Degrees of belief can be ordered; if $\bel(A)$ is ‘greater’ than $\bel(B)$, and $\bel(B)$ is ‘greater’ than $\bel(C)$, then $\bel(A)$ is ‘greater’ than $\bel(C)$.
[Consequence: beliefs can be mapped onto real numbers.]
- The degree of belief in a proposition $A$ and its negation $\bar{A}$ are related. There is a function $f$ such that 

$$\bel(\bar{A}) = f(\bel(A)).$$

- The degree of belief in a conjunction of propositions $x, y$ ($x$ $\texttt{AND}$ $y$) is related to the degree of belief in the conditional proposition $x \vert y$ and the degree of belief in the proposition $y$. There is a function $g$ such that

$$\bel(A,B) = g(\bel(A \mid B), \bel(B)).$$

From these axioms it follows (skipping some details) that degrees of belief must follow the same rules as probability theory. That is,

$$
\begin{align*}
    \bel(\texttt{TRUE}) &= 1 \\
    \bel(\texttt{FALSE}) &= 0 \\
    \bel(\bar{A}) &= 1 - \bel(A)  &&\textit{sum rule}\\
    \bel(A,B) &= \bel(A|B) \bel(B)  &&\textit{product rule}
\end{align*} 
$$

We will therefore use the symbol $P$ instead of $\bel$ from now on.  

From these rules we get the extended sum rule.

$$
\begin{align*}
    P(A+B) = P(A) + P(B) - P(AB)
\end{align*}
$$

### Applications

#### Extension of the logical implication

The extension of the statement $A \implies B$ for uncertain propositions is the following:  

$$P(B \mid A) > P(A).$$

Recall that in (classical) logic we were not able to deduce from this that $B \implies A$. However, in the extended setting we do have (see Appendix)

$$P(B \mid A) > P(A) \implies P(A \mid B) > P(B).$$

Using our earlier example, this translates to the fact that observing that it is cloudy before 10 will make it more likely that it will rain at 10. 

#### Bayes' rule 

We want to see how our belief about a certain hypothesis $H$ changes after observing datum $D$, given background information $X$. From the product and sum rule above we have get

$$ P(H \mid D, X) = \frac{P(D \mid H, X) P(H \mid X)}{P(D|X)}, $$

with

$$P(D \mid X) = P(D \mid H, X) P(H \mid X) + P(D \mid \bar{H}, X) P(\bar{H} \mid X).$$ 

We can rewrite this as follows:

$$ P(H \mid D, X) = \frac{P(D \mid H, X) }{P(D \mid X) } P(H \mid X).$$

Note that this is of the form: `posterior = factor * prior`. If `factor` is bigger than one, the data increases our belief in $H$, and if `factor` is smaller than one, our belief is decreased. It is interesting to note that whether `factor` is bigger or smaller than one is fully determined by the ratio of $P(D \mid H, X)$ and $P(D \mid \bar{H}, X)$. This can be more clearly seen by writing the log odds

$$ \log \frac{P(H \mid D, X)}{P(\bar{H} \mid D, X)} = \log \frac{P(H \mid X)}{P(\bar{H} \mid X)} + \log \frac{P(D \mid H, X)}{P(D \mid \bar{H}, X)}. $$

The posterior log odds are increased by the amount $\log \frac{P(D \mid H, X)}{P(D \mid \bar{H}, X)}$.

#### Two urns

Consider two urns.  
Urn A contains 2 black balls and 1 white ball  
Urn B contains 2 white balls and 1 black ball.  
You select one urn at random and draw a ball from the urn and observe that it is black. What is your (posterior) belief about having selected urn A? 

Let us denote the proposition of having selected urn A by $A$, the data $D$, and the background information $I$. We can assign our prior belief, and the likelihood of the data using the principle of indifference. 

$$
\begin{align*}
    P(A|I) &= 1/2 \\
    P(D|AI) &= 2/3 \\
    P(D|\bar{A}I) &= 1/3
\end{align*}
$$

Using Bayes' rule derived above we get 

$$
\begin{align*}
    P(A|DI) &=\frac{P(D|AI)}{P(D|AI)P(A|I) + P(D|\bar{A}I)P(\bar{A}|I)}  P(A|I)\\
    &= \frac{2/3}{2/3 * 1/2 + 1/3 * 1/2} * 1/2 \\
    &= 2/3
\end{align*}
$$

or in terms of log odds 

$$
\begin{align*} 
    \log \frac{P(A \mid D, I)}{P(\bar{A} \mid D, I)} &= \log \frac{P(A \mid I)}{P(\bar{A} \mid I)} + \log \frac{P(D \mid A, I)}{P(D \mid \bar{A}, I)} \\
    &= 0 + \log(2)
\end{align*}
$$


## Appendix

#### Extension of logical implication

$$
\begin{align*}
    P(A|B) &= \frac{P(AB)}{P(B)} \\
    &> \frac{P(AB)}{P(B|A)} \\
    &= \frac{P(B|A)P(A)}{P(B|A)}\\
    &= P(A)
\end{align*}
$$

Note also that this does not contradict the classical case, 

$$ (A \implies B) \not\implies (B \implies A). $$

$A \implies B$ corresponds to $P(B \mid A) = 1$. However, this says nothing about $P(A \mid B)$ being equal to one or not. 