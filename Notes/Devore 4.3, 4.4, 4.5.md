### Chapter 4.3
- A continuous rv $X$ is said to have a normal distribution with parameters $m$ and $s$ (or $m$ and $s^2$), where $-\infty < m < \infty$ and $0 < s$, if the pdf of $X$ is
$$ f(x; m, s) = \frac{1}{\sqrt{2\pi s}} \exp\left(-\frac{(x-m)^2}{2s^2}\right) \quad -\infty < x < \infty $$
- The normal distribution with parameter values $m = 0$ and $s = 1$ is called the standard normal distribution. A random variable having a standard normal distribution is called a standard normal random variable and will be denoted by $Z$. The pdf of $Z$ is
$$ f(z; 0, 1) = \frac{1}{\sqrt{2\pi}} \exp\left(-\frac{z^2}{2}\right) \quad -\infty < z < \infty $$
The graph of $f(z; 0, 1)$ is called the standard normal (or z) curve. Its inflection points are at $1$ and $-1$. The cdf of $Z$ is 
$$ P(Z \leq z) = \int_{-\infty}^{z} f(y; 0, 1) \, dy $$
which we will denote by $F(z)$.
- If $X$ has a normal distribution with mean $m$ and standard deviation $s$, then
$$ Z = \frac{X - m}{s} $$
has a standard normal distribution. Thus
$$ P(a \leq X \leq b) = P\left(\frac{a - m}{s} \leq Z \leq \frac{b - m}{s}\right) = F\left(\frac{b - m}{s}\right) - F\left(\frac{a - m}{s}\right) $$
$$ P(X \leq a) = F\left(\frac{a - m}{s}\right) $$
$$ P(X \geq b) = 1 - F\left(\frac{b - m}{s}\right) $$
- If the population distribution of a variable is (approximately) normal, then
	- Roughly 68% of the values are within 1 SD of the mean. 
	- Roughly 95% of the values are within 2 SDs of the mean. 
	- Roughly 99.7% of the values are within 3 SDs of the mean
- The $(100p)$th percentile for normal $(m, s)$ is 
$$ m + \left( \text{(100p)th for standard normal} \right) \times s $$
- Let $X$ be a binomial rv based on $n$ trials with success probability $p$. Then if the binomial probability histogram is not too skewed, $X$ has approximately a normal distribution with $m = np$ and $s = \sqrt{npq}$. In particular, for $x$ a possible value of $X$,
$$ P(X \leq x) = B(x, n, p) \approx {\text{area under the normal curve to the left of } x + 0.5} = F\left( \frac{x + 0.5 - np}{\sqrt{npq}} \right) $$
### Chapter 4.4
- $X$ is said to have an exponential distribution with (scale) parameter $\lambda$ ($\lambda > 0$) if the pdf of $X$ is
$$ f(x; \lambda) = 
\begin{cases} 
\lambda e^{-\lambda x} & \text{for } x \geq 0 \\
0 & \text{otherwise}
\end{cases} $$
- For the cumulative distribution function (cdf) $F(x; \lambda)$ of an exponential distribution:
$$ F(x; \lambda) = 
\begin{cases} 
0 & \text{for } x < 0 \\
1 - e^{-\lambda x} & \text{for } x \geq 0 
\end{cases} $$

- For the mean and variance:
$$ m = \frac{1}{\lambda} $$
$$ s^2 = \frac{1}{\lambda^2} $$
### Chapter 4.4
- For \(a > 0\), the gamma function \(G(a)\) is defined by:
$$ G(a) = \int_{0}^{\infty} x^{a-1} e^{-x} dx$$
The most important properties of the gamma function are the following:
1. For any \(a > 1\), $$ G(a) = (a - 1) \cdot G(a - 1) $$
2. For any positive integer, \(n\), $$ G(n) = (n - 1)! $$
3. $$ G\left(\frac{1}{2}\right) = \sqrt{\pi} $$
- A continuous random variable \(X\) is said to have a gamma distribution if the pdf of \(X\) is:
$$
f(x; a, b) = \begin{cases}
\frac{1}{b^a G(a)} x^{a-1} e^{-\frac{x}{b}} & \text{for } x \geq 0 \\
0 & \text{otherwise}
\end{cases}
$$
where the parameters \(a\) and \(b\) satisfy \(a > 0\), \(b > 0\). The standard gamma distribution has \(b = 1\).
### Chapter 4.5
- 
