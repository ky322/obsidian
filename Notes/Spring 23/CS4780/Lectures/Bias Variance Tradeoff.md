Given dataset $D = \{(\mathbf{x}_1, y_1), \dots, (\mathbf{x}_n,y_n)\}$ drawn i.i.d from some distribution $P(X,Y)$
Assume a regression setting $y\in\mathbb{R}$
Consider for any input $\vec{x}$ there may not be a unique label $y$

### Expected label
Given $\vec{x}\in\mathbb{R}^d$
$$\bar{y}(\mathbf{x}) = E_{y \vert \mathbf{x}} \left[Y\right] = \int\limits_y y \, \Pr(y \vert \mathbf{x}) \partial y$$
The expected label is the label we expect to obtain given feature vector $\vec{x}$

### Expected Test Error 
Given $h_D$
1. We draw our training set $D$ of $n$ inputs and i.i.d from distribution $P$ 
2. Call some ML algorithm $\mathcal{A}$ on this data set to learn a hypothesis $h_D=\mathcal{A}(D)$
For a given $h_D$, learned on data set $D$ with algorithm $\mathcal{A}$, we can compute the generalization error $$E_{(\mathbf{x},y) \sim P} \left[ \left(h_D (\mathbf{x}) - y \right)^2 \right] = \int\limits_x \! \! \int\limits_y \left( h_D(\mathbf{x}) - y\right)^2 \Pr(\mathbf{x},y) \partial y \partial \mathbf{x}$$
### Expected Classifier 
Given $\mathcal{A}$
$$\bar{h} = E_{D \sim P^n} \left[ h_D \right] = \int\limits_D h_D \Pr(D) \partial D$$
### Expected Test Error 
Given $\mathcal{A}$
$$\begin{equation*}
E_{\substack{(\mathbf{x},y) \sim P\\ D \sim P^n}} \left[\left(h_{D}(\mathbf{x}) - y\right)^{2}\right] = \int_{D} \int_{\mathbf{x}} \int_{y} \left( h_{D}(\mathbf{x}) - y\right)^{2} \mathrm{P}(\mathbf{x},y) \mathrm{P}(D) \partial \mathbf{x} \partial y \partial D
\end{equation*}$$
## Decomposition of Expected Test Error

$$\begin{align}
	E_{\mathbf{x},y,D}\left[\left[h_{D}(\mathbf{x}) - y\right]^{2}\right] &= E_{\mathbf{x},y,D}\left[\left[\left(h_{D}(\mathbf{x}) - \bar{h}(\mathbf{x})\right) + \left(\bar{h}(\mathbf{x}) - y\right)\right]^{2}\right] \nonumber \\
    &= E_{\mathbf{x}, D}\left[(\bar{h}_{D}(\mathbf{x}) - \bar{h}(\mathbf{x}))^{2}\right] + 2 \mathrm{\;} E_{\mathbf{x}, y, D} \left[\left(h_{D}(\mathbf{x}) - \bar{h}(\mathbf{x})\right)\left(\bar{h}(\mathbf{x}) - y\right)\right] + E_{\mathbf{x}, y} \left[\left(\bar{h}(\mathbf{x}) - y\right)^{2}\right]
\end{align}$$
Steps for Reference:
1. Add and subtract $\bar{h}(\vec{x})$
2. Expand the square using $a^2+ab+b^2$

Middle Term
$$\begin{align*}
	E_{\mathbf{x}, y, D} \left[\left(h_{D}(\mathbf{x}) - \bar{h}(\mathbf{x})\right) \left(\bar{h}(\mathbf{x}) - y\right)\right] &= E_{\mathbf{x}, y} \left[E_{D} \left[ h_{D}(\mathbf{x}) - \bar{h}(\mathbf{x})\right] \left(\bar{h}(\mathbf{x}) - y\right) \right] \\
    &= E_{\mathbf{x}, y} \left[ \left( E_{D} \left[ h_{D}(\mathbf{x}) \right] - \bar{h}(\mathbf{x}) \right) \left(\bar{h}(\mathbf{x}) - y \right)\right] \\
    &= E_{\mathbf{x}, y} \left[ \left(\bar{h}(\mathbf{x}) - \bar{h}(\mathbf{x}) \right) \left(\bar{h}(\mathbf{x}) - y \right)\right] \\
    &= E_{\mathbf{x}, y} \left[ 0 \right] \\
    &= 0
\end{align*}$$

Steps for Reference:
1. Use Law of Total Expectation to separate the expectation over $D$ and the expectation over $\vec{x}$ and $y$. 
2. Apply linearity of expectation
3. $\bar{h}(\vec{x})$ does not depend on the dataset $D$
$$\begin{align*}
	E_{\mathbf{x}, y, D} \left[ \left( h_{D}(\mathbf{x}) - y \right)^{2} \right] = \underbrace{E_{\mathbf{x}, D} \left[ \left(h_{D}(\mathbf{x}) - \bar{h}(\mathbf{x}) \right)^{2} \right]}_\mathrm{Variance} + E_{\mathbf{x}, y}\left[ \left( \bar{h}(\mathbf{x}) - y \right)^{2} \right]
\end{align*}$$
Second Term
$$\begin{align}
	E_{\mathbf{x}, y} \left[ \left(\bar{h}(\mathbf{x}) - y \right)^{2}\right] &= E_{\mathbf{x}, y} \left[ \left(\bar{h}(\mathbf{x}) -\bar y(\mathbf{x}) )+(\bar y(\mathbf{x}) - y \right)^{2}\right]  \\
  &=\underbrace{E_{\mathbf{x}, y} \left[\left(\bar{y}(\mathbf{x}) - y\right)^{2}\right]}_\mathrm{Noise} + \underbrace{E_{\mathbf{x}} \left[\left(\bar{h}(\mathbf{x}) - \bar{y}(\mathbf{x})\right)^{2}\right]}_\mathrm{Bias^2} + 2 \mathrm{\;} E_{\mathbf{x}, y} \left[ \left(\bar{h}(\mathbf{x}) - \bar{y}(\mathbf{x})\right)\left(\bar{y}(\mathbf{x}) - y\right)\right]
\end{align}$$
Steps:
1. Same trick with expansion by adding and subtracting same term
2. Expand with $a^2+ab+b^2$

Third Term
$$\begin{align*}
	E_{\mathbf{x}, y} \left[\left(\bar{h}(\mathbf{x}) - \bar{y}(\mathbf{x})\right)\left(\bar{y}(\mathbf{x}) - y\right)\right]
    &= E_{\mathbf{x}} \left[ E_{y \mid \mathbf{x}} \left[ \bar{y}(\mathbf{x}) - y\right] \left(\bar{h}(\mathbf{x}) - \bar{y}(\mathbf{x})\right)\right] \\
    &= E_{\mathbf{x}} \left[ \left( \bar{y}(\mathbf{x}) - E_{y \mid \mathbf{x}} \left [ y \right]\right) \left(\bar{h}(\mathbf{x}) - \bar{y}(\mathbf{x})\right)\right] \\
    &= E_{\mathbf{x}} \left[ \left( \bar{y}(\mathbf{x}) - \bar{y}(\mathbf{x}) \right) \left(\bar{h}(\mathbf{x}) - \bar{y}(\mathbf{x})\right)\right] \\
    &= E_{\mathbf{x}} \left[ 0 \right] \\
    &= 0
\end{align*}$$
Steps:
1. Use Law of iterated expectations
2. Constant so we can move it out 
3. Becomes y bar somehow
$$\begin{equation*}
	\underbrace{E_{\mathbf{x}, y, D} \left[\left(h_{D}(\mathbf{x}) - y\right)^{2}\right]}_\mathrm{Expected\;Test\;Error} = \underbrace{E_{\mathbf{x}, D}\left[\left(h_{D}(\mathbf{x}) - \bar{h}(\mathbf{x})\right)^{2}\right]}_\mathrm{Variance} + \underbrace{E_{\mathbf{x}, y}\left[\left(\bar{y}(\mathbf{x}) - y\right)^{2}\right]}_\mathrm{Noise} + \underbrace{E_{\mathbf{x}}\left[\left(\bar{h}(\mathbf{x}) - \bar{y}(\mathbf{x})\right)^{2}\right]}_\mathrm{Bias^2}
\end{equation*}$$
**Variance**: How much our classifier changes if you train on a different training set. Checks if our classifier overfits for a particular training set
**Bias**: Inherent error we obtain from our classifier even with infinite training data. Inherent to our model
**Noise**: Data intrinsic noise. Measures ambiguity due to data distribution and feature representation. An aspect of data

## Detecting High Bias and High Variance 

If a classifier is underperforming (the test or training error is too high):
![[Bias Variance Graph.png]]

This graph plots the training error and the test error:
- In the first regime, the training error is below the desired error threshold $\epsilon$ but the test error is significantly higher
- In the second regime, both are above $\epsilon$

### Regime 1: High Variance 

Symptoms:
1. Training error is much lower than test error
2. Training error is lower than $\epsilon$
3. Test error is above $\epsilon$

Solutions:
- Add more training data
- Reduce model complexity; Complex models are prone to high variance 
- Bagging

### Regime 2: High Bias

The model is not robust enough to produce an accurate prediction 

Symptoms:
1. Training error is higher than $\epsilon$

Solutions:
- Use a more complex model
- Add features
- Bossting