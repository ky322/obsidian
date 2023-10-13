### Chapter 4.1
- Let $X$ be a continuous rv. Then a probability distribution or probability density function (pdf) of $X$ is a function $f(x)$ such that for any two numbers $a$ and $b$ with $a\leq b$,
$$ P(a \leq X \leq b) = \int_{a}^{b} f(x) \, dx $$
That is, the probability that $X$ takes on a value in the interval $[a, b]$ is the area above this interval and under the graph of the density function. The graph of $f(x)$ is often referred to as the density curve.
- A continuous rv $X$ is said to have a uniform distribution on the interval $[A, B]$ if the pdf of $X$ is
$$ f(x; A, B) = \begin{cases} 
\frac{1}{B - A} & \text{if } A \leq x \leq B \\
0 & \text{otherwise} 
\end{cases} $$
### Chapter 4.2
- The cumulative distribution function $F(x)$ for a continuous rv $X$ is defined for every number $x$ by
$$ F(x) = P(X \leq x) = \int_{-\infty}^{x} f(y) \, dy $$
For each $x$, $F(x)$ is the area under the density curve to the left of $x$. 
- Let $X$ be a continuous rv with pdf $f(x)$ and cdf $F(x)$. Then for any number $a$,
$$ P(X > a) = 1 - F(a) $$
and for any two numbers $a$ and $b$ with $a < b$,
$$ P(a \leq X \leq b) = F(b) - F(a) $$
- If $X$ is a continuous rv with pdf $f(x)$ and cdf $F(x)$, then at every $x$ at which the derivative $F'(x)$ exists, 
$$ F'(x) = f(x) $$
- Let $p$ be a number between 0 and 1. The $(100p)$th percentile of the distribution of a continuous rv $X$, denoted by $h(p)$, is defined by
$$ p = F(h(p)) = \int_{-\infty}^{h(p)} f(y) \, dy $$
- The expected or mean value of a continuous rv $X$ with pdf $f(x)$ is
$$ mX = E(X) = \int_{-\infty}^{\infty} x \cdot f(x) \, dx $$
- If $X$ is a continuous rv with pdf $f(x)$ and $h(X)$ is any function of $X$, then
$$ E[h(X)] = m_{h(X)} = \int_{-\infty}^{\infty} h(x) \cdot f(x) \, dx $$
- The variance of a continuous random variable $X$ with pdf $f(x)$ and mean value $m$ is
$$ s_X^2 = V(X) = \int_{-\infty}^{\infty} (x - m)^2 \cdot f(x) \, dx = E[(X - m)^2] $$
- The standard deviation (SD) of $X$ is 
$$ s_X = \sqrt{V(X)} $$

