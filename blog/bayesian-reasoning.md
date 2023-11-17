---
layout: post
author: jesse
title: Bayesian Reasoning
header-includes: \mid 
    \usepackage{mymacros}
---

# Bayesian Reasoning    

We want to see how our belief about a certain hypothesis $H$ changes after observing datum $D$, given background information $X$. 

$$ P(H \mid D, X) = \frac{P(D \mid H, X) P(H \mid X)}{P(D|X)}, $$

where $P(D \mid X) = P(D \mid H, X) P(H \mid X) + P(D \mid \bar{H}, X) P(\bar{H} \mid X)$. We can therefore rewrite as follows:

$$ P(H \mid D, X) = \frac{P(D \mid H, X) }{P(D \mid H, X) P(H \mid X) + P(D \mid \bar{H}, X) P(\bar{H} \mid X)} P(H \mid X).$$

Note that this is of the form: `posterior = factor * prior`, where `factor` = $\frac{P(D \mid H, X) }{P(D \mid H, X) P(H \mid X) + P(D \mid \bar{H}, X) P(\bar{H} \mid X)}$. If `factor` is bigger than one, the data increases our belief in $H$, and if `factor` is smaller than one, our belief is decreased. It is interesting to note that whether `factor` is bigger or smaller than one is fully determined by the ratio of $P(D \mid H, X)$ and $P(D \mid \bar{H}, X)$. This can be more clearly seen by writing the log odds

$$ \log \frac{P(H \mid D, X)}{P(\bar{H} \mid D, X)} = \log \frac{P(H \mid X)}{P(\bar{H} \mid X)} + \log \frac{P(D \mid H, X)}{P(D \mid \bar{H}, X)}. $$

The posterior log odds are increased by the amount $\log \frac{P(D \mid H, X)}{P(D \mid \bar{H}, X)}$.