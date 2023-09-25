>[!info]
>**Recall**:
>Generative: Estimate $P(\vec{x_i},y)$
>Discrimative: Model $P(y|\vec{x_i})$

Naïve Bayes is Generative
- Models $P(\vec{x_i}|y)$ 
- Makes assumptions on its distribution (categorical, multinomial, or Gaussian)
- Parameters are estimated with MLE or MAP

Logistic Regression is Discrimative
- Model $P(y|\vec{x_i})$
	- Assume it takes the form: $P(y|\vec{x}_i)=\dfrac{1}{1+e^{-y(\vec{w}^T \vec{x}_i+b)}}$
## Maximum Likelihood Estimate (MLE)

Choose parameters that maximize the conditional likelihood $P(\vec{y}|X,\vec{w})$, which is the probability of the observed values $\vec{y}\in\mathbb{R}^n$ in the training data conditioned on the feature values $x_i$ where $X=\left[\mathbf{x}_1, \dots,\mathbf{x}_i, \dots, \mathbf{x}_n\right] \in \mathbb R^{d \times n}$

Assume $y_i$ are independent given the features $\vec{x_i}$ and $\vec{w}$

$$\begin{aligned}
\hat{\vec{w}}_{MLE} &= 
\operatorname*{argmax}_{\vec{w}} P(D|\vec{w})\\
&= \operatorname*{argmax}_{\vec{w}}P((y_1,\vec{x}_1),\dots,(y_n,\vec{x}_n) \mid  \vec{w})\\
&=\operatorname*{argmax}_{\vec{w}}\prod_{i=1}^n P(y_i,\vec{x}_i \mid  \vec{w}) \\
&=\operatorname*{argmax}_{\vec{w}}\prod_{i=1}^n P(y_i \mid  \vec{x}_i,\vec{w})P(\vec{x}_i \mid \vec{w})\\
&=\operatorname*{argmax}_{\vec{w}}\prod_{i=1}^n P(y_i \mid  \vec{x}_i,\vec{w})P(\vec{x}_i)\\
&=\operatorname*{argmax}_{\vec{w}}\prod_{i=1}^n P(y_i \mid  \vec{x}_i,\vec{w})\\
&=\operatorname*{argmax}_{\vec{w}}\sum_{i=1}^n\log\left[ P(y_i \mid \vec{x}_i, \vec{w})\right]\\
&=\operatorname*{argmax}_{\vec{w}} -\sum_{i=1}^n \log(1+e^{-y_i \vec{w}^T \vec{x}_i})\\
&=\operatorname*{argmin}_{\mathbf{w}}\sum_{i=1}^n \log(1+e^{-y_i \mathbf{w}^T \mathbf{x}_i})
\end{aligned}$$
Steps For Reference
1. Definition of MLE
2. Substitute in D 
3. Data is i.i.d
4. Chain Rule of Statistics
5. $\vec{x_i}$ does not depend on $\vec{w}$
6. $P(\vec{x_i})$ does not affect $\vec{w}$
7. Take the log
8. Substitute in $P(y_i|\vec{x_i},\vec{w})$
9. We prefer minimization

Use Gradient Descent on the negative log likelihood $\ell(\mathbf{w})=\sum_{i=1}^n \log(1+e^{-y_i \mathbf{w}^T \mathbf{x}_i})$ because there is no closed form solution

## MAP Estimate 

Treat $\vec{w}$ as a random variable and specify a prior belief distribution over it. 

**Goal:** Find the most likely model parameter given the data; the parameter that maximizes the posterior
$\begin{align}P(\vec{w} \mid D) = P(\vec{w} \mid X, \mathbf y) &\propto P(\vec{y}\mid X, \vec{w}) \; P(\vec{w})\end{align}$

Solve for $\hat{\vec{w}}_{MAP}$ $$\begin{aligned}
\hat{\mathbf{w}}_{MAP} &= \operatorname*{argmax}_{\vec{w}} P(D|\vec{w})P(\vec{w})\\
&= \operatorname*{argmax}_{\vec{w}}P((y_1,\vec{x}_1),\dots,(y_n,\vec{x}_n) \mid \vec{w})P(\vec{w})\\
&=\operatorname*{argmax}_{\vec{w}}\left(\prod_{i=1}^n P(y_i \mid  \vec{x}_i,\mathbf{w})\right)P(\vec{w}\\
&=\operatorname*{argmax}_{\vec{w}}\sum_{i=1}^n\log\left[ P(y_i \mid \vec{x}_i, \vec{w})\right]+\log P(\vec{w})  \\
&=\operatorname*{argmin}_{\vec{w}}-\sum_{i=1}^n\log\left[ P(y_i \mid \vec{x}_i, \vec{w})\right]-\log P(\vec{w})\\
&=\operatorname*{argmin}_{\vec{w}}\sum_{i=1}^n\log\left[1+e^{-y_i \vec{w}^T \vec{x}_i}\right]+\frac{1}{2\sigma^2}\vec{w}^\top\vec{w} \\

&=\operatorname*{argmin}_{\vec{w}}\sum_{i=1}^n\log\left[1+e^{-y_i \mathbf{w}^T \vec{x}_i}\right]+\lambda\vec{w}^\top\vec{w} \\
\end{aligned}$$
Steps For Referene:
1. Definition of MAP
2. Substitute in D 
3. Data is i.i.d
4. Take the log
5. We prefer minimization
6. Substitute in $P(y_i|\vec{x_i},\vec{w})$ and $P(\vec{w})$
7. Substitute in $P(y_i|\vec{x_i},\vec{w})$ and use $L_2$ regularization

To find optimal parameter $\vec{w}$ we use Gradient Descent on the negative log posterior $\displaystyle\ell(\vec{w})=\sum_{i=1}^n \log(1+e^{-y_i\vec{w}^T\vec{x}_i})+\lambda\vec{w}^\top\vec{w}$

## Summary

- Logistic Regression is the discrimative counterpart to Naive Bayes
- Naive Bayes: Model $P(\vec{x}|y)$ for each label $y$ and then get the decision boundary that discriminates between the two distribution
- Logistic Regression: Model $P(y|\vec{x})$ directly
	- Assume probabilistic form: $P(y|\vec{x}_i)=\dfrac{1}{1+e^{-y(\vec{w}^T \vec{x}_i+b)}}$
	- Flexible but needs more data to avoid overfitting
- If we have little data, choose Naive Bayes
- If we have large data, Logistic Regression outperforms Naive Bayes since we suffer from the assumptions made about $P(\vec{x}|y)$
- If the assumption holds exactly, the data is drawn from the distributioin we assumed in Naive Bayes then logistic regression and Naive Bayes converge to the same result, but Naive Bayes will be faster.