### Chapter 3.1
- Random Variable: A rule that associates a number with each outcome in $S$ for a given sample same $S$ of some experiment; A function whose domain is in the sample space and whose range is the set of real numbers
	- Discrete: The possible values either constitute a finite set or is countably infinite
	- Continuous: Its set of possible values consists either of all numbers in a single interval or all numbers in a disjoint union of such intervals AND no possible value of the variable has positive probability 
- Bernoulli Random Variable: Any random variable whose only possible values are 0 and 1
### Chapter 3.2
- The probability distribution or probability mass function (pmf) of a discrete random variable is defined for every number $x$ by: $$\begin{equation} p(x) = P(X = x) = P(\{ v \in S : X(v) = x \}) \end{equation}$$
-  The cumulative distribution function (cdf) $F(x)$ of a discrete random variable $X$ with probability mass function (pmf) $p(x)$ is defined for every number $x$ by:
$$
F(x) = P(X \leq x) = \sum_{y \leq x} p(y)
$$
For any number x, $F(x)$ is the probability that the observed value of X will be at most x.
$$F(x) = P(X \leq x) = \sum_{y \leq x} p(y)$$
$$P(a\leq X\leq b)=F(b)-F(a-1)$$
If a=b then $$P(X=a)=F(a)-F(a-1)$$
### Chapter 3.3
- Let $X$ be a discrete rv with a set of possible values $D$ and pmf $p(x)$. The expected value or mean value of $X$, denoted by $E(X)$ or $\mu_X$ or just $\mu$, is:
$$E(X) = \mu_X = \sum_{x \in D} x \cdot p(x)$$
- If the rv $X$ has a set of possible values $D$ and pmf $p(x)$, then the expected value of any function $h(X)$, denoted by $E[h(X)]$ or $\mu h(X)$, is computed by:
$$E[h(X)] = \sum_{x \in D} h(x) \cdot p(x)$$
- $$E(aX + b) = a \cdot E(X) + b$$
- Let $X$ have pmf $p(x)$ and expected value $m$. Then the variance of $X$, denoted by $V(X)$ or $s_X^2$, or just $s^2$, is:
$$V(X) = \sum_{x \in D} (x - m)^2 \cdot p(x) = E[(X - m)^2]$$
- The standard deviation (SD) of $X$ is:
$$s_X = \sqrt{s_X^2}, \sigma=\sqrt{V(X)}$$
- $$V(X) = s^2 = \sum_{x \in D} x^2 \cdot p(x) - m^2 = E(X^2) - [E(X)]^2$$
- $$ V(aX + b) = s_{aX+b}^2 = a^2 \cdot s_X^2 , s_{aX+b} = |a| \cdot s_X $$In particular,
$$ s_{aX} = |a| \cdot s_X,  s_{X+b} = s_X  $$
