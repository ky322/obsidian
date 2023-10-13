### Chapter 3.4
#### Binomial Experiment
1. The experiment consists of a sequence of n smaller experiments called trials, where n is fixed in advance of the experiment. 
2. Each trial can result in one of the same two possible outcomes (dichotomous  trials), which we generically denote by success (S) and failure (F). The assignment of the S and F labels to the two sides of the dichotomy is arbitrary.
3. The trials are independent, so that the outcome on any particular trial does not influence the outcome on any other trial. 
4. The probability of success P(S) is constant from trial to trial; we denote this probability by p

- The binomial random variable $X$ associated with a binomial experiment consisting of $n$ trials is defined as:
$$X = \text{the number of S’s among the $n$ trials}$$
- Because the pmf of a binomial rv $X$ depends on the two parameters $n$ and $p$, we denote the pmf by $b(x; n, p)$.
- $$
b(x; n, p) = 
\begin{cases} 
\binom{n}{x} p^x (1 - p)^{n-x} & \text{for } x = 0, 1, 2, \ldots, n \\
0 & \text{otherwise}
\end{cases}
$$
### Chapter 3.5
#### Hypergeometric Distribution
1. The population or set to be sampled consists of N individuals, objects, or elements (a finite population). 
2. Each individual can be characterized as a success (S) or a failure (F), and there are M successes in the population. 
3. A sample of n individuals is selected without replacement in such a way that each subset of size n is equally likely to be chosen.
- If \(X\) is the number of S’s in a completely random sample of size \(n\) drawn from a population consisting of \(M\) S’s and \(N - M\) F’s, then the probability distribution of \(X\), called the hypergeometric distribution, is given by:
$$
P(X = x) = h(x; n, M, N) = \frac{\binom{M}{x} \binom{N - M}{n - x}}{\binom{N}{n}}
$$
for \(x\) an integer satisfying \(\max(0, n - N + M) \leq x \leq \min(n, M)\).
- The mean and variance of the hypergeometric rv $X$ having pmf $h(x; n, M, N)$ are:
$$
E(X) = n \cdot \frac{M}{N}
$$
and
$$
V(X) = \frac{(N - n)(nM)(N-M)}{N^2(N-1)}
$$
### Chapter 3.6
#### Poisson Distribution
- A discrete random variable \(X\) is said to have a Poisson distribution with parameter \(m\) (\(m > 0\)) if the pmf of \(X\) is:
$$
p(x; m) = \frac{e^{-m} \cdot m^x}{x!} \quad \text{for } x = 0, 1, 2, 3, \ldots
$$
- Suppose that in the binomial pmf $b(x; n, p)$, we let $n \to \infty$ and $p \to 0$ in such a way that $np$ approaches a value $m > 0$. Then $b(x; n, p) \to p(x; m)$.
- If $X$ has a Poisson distribution with parameter $m$, then $E(X) = V(X) = m$.
