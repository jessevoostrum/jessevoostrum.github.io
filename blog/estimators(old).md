
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