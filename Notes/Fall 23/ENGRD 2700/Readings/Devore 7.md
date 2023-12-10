### Chapter 7.1
- Suppose our parameter of interest is a population mean $\mu$ and 
	1. The population distribution is normal
	2. The value of the population standard deviation $\sigma$ is known
- Given the sample mean $\bar{x}$ the 95% confidence interval for $\mu$ $$\left(\bar{x}-1.96\frac{\sigma}{\sqrt{n}},\bar{x}+1.96\frac{\sigma}{\sqrt{n}}\right)$$ The probability is 0.95 that the random interval includes or covers the true value of $\mu$
- A $100(1-\alpha)\%$ confidence interval for $\mu$ of a normal population when we know $\sigma$ $$\left(\bar{x}-z_{\alpha/2}\frac{\sigma}{\sqrt{n}},\bar{x}+z_{\alpha/2}\frac{\sigma}{\sqrt{n}}\right)$$
- The gain in reliability entails a loss in precision
- The size necessary for the CI to have a width w $$n=(2z_{\alpha/2}\frac{\sigma}{w})^2$$
### Chapter 7.2
- If n is large n>40 the standardized variable $$Z=\frac{\bar{X}-\mu}{S/\sqrt{n}}$$ takes approximately a standard normal distribution
### Chapter 7.3
- When $\bar{X}$ is the mean of a random sample of size n from a normal distribution with mean $\mu$
 the RV $$T=\frac{\bar{X}-\mu}{S/\sqrt{n}}$$has a t distribution with n-1 degrees of freedom
 - Let $t_v$ denote the t distribution with v df
	 1. Each $t_v$ curve is bell shaped and centered at 0
	 2. Each $t_v$ curve is more spread out than the standard normal z curve
	 3. As v increases the spread of the $t_v$ curve decreases
	 4. As $v\rightarrow\infty$ the curve approaches the standard normal curve
- T Critical Value: $t_{a,v}$ the number on the measurement axis where the area under the t curve with v df to the right of $t_{a,v}$ is $\alpha$
- Given the sample mean and sample standard deviation from a random sample from a normal population with mean $\mu$. A $100(1-\alpha)\%$ confidence interval for $\mu$  $$\left(\bar{x}-t_{\alpha/2,n-1}\frac{\sigma}{\sqrt{n}},\bar{x}+t_{\alpha/2,n-1}\frac{\sigma}{\sqrt{n}}\right)$$
