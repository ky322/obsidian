### Chapter 8.1
- $H_0$ is the claim that is initially assumed to be true. $H_1$ is the assertion that contradicts $H_0$. We can reject $H_0$ or fail to reject $H_0$
- p-value: The probability of obtaining a value of the test statistic at least as contradictory to $H_0$ as the value calculated from the available sample data
	- $H_0$ will be rejected in favor of $H_1$ if $p\leq\alpha$
- A type I error consists of rejecting the mull hypothesis $H_0$ when it is true
	- P(Type I Error) $=\alpha$
- A type II error consists of not rejecting $H_0$ when it is false
### Chapter 8.2
Assuming we have a normal population distribution with known value of $\sigma$
- $H_0:\mu=\mu_0$
- Test Statistic: $T=\frac{\bar{X}-\mu_0}{\sigma/\sqrt{n}}$
- $H_1: \mu>\mu_0$ Area under the standard normal curve to the right of z 
- $H_2: \mu<\mu_0$ Area under the standard normal curve to the left of z 
- $H_3: \mu\neq\mu_0$ 2 * Area under the standard normal curve to the right of $|z|$
1. Identify parameter of interest and describe it in the context of the problem
2. Determine null value and state null hypothesis
3. State appropriate alternative hypothesis
4. Give formula for computed value of the test statistic
5. Compute any sample quantities substitute into the formula for the test statistic value and compute
6. Determine p-value
7. Compare significance level to the p-value to decide whether to reject $H_0$
- The sample size n for which a level $\alpha$ test also has $\beta(\mu')=\beta$ $$n=\left[\frac{\sigma(z_\alpha+z_\beta)}{\mu_0-\mu_1}\right]^2$$ for a one sided test
![[Pasted image 20231207045251.png]]
### Chapter 8.3
Assuming we have a normal population distribution
- $H_0:\mu=\mu_0$
- Test Statistic: $t=\frac{\bar{X}-\mu_0}{s/\sqrt{n}}$
- $H_1: \mu>\mu_0$ Area under the $t_{n-1}$ curve to the right of t
- $H_2: \mu<\mu_0$ Area under the $t_{n-1}$ curve to the left of t
- $H_3: \mu\neq\mu_0$ 2 * Area under the $t_{n-1}$ curve to the right of $|t|$
### Chapter 8.4
Population proportions
- $H_0:p=p_0$
- Test Statistic: $z=\frac{\hat{p}-p_0}{\sqrt{p_0(1-p_0)/n}}$
- $H_1: p>p_0$ Area under the standard normal curve to the right of z 
- $H_2: p<p_0$ Area under the standard normal curve to the left of z 
- $H_3: p\neq p_0$ 2 * Area under the standard normal curve to the right of $|z|$
- 