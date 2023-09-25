## Assumptions
Data: $y_i\in\mathbb{R}$
Model Assumption: $y_i=\vec{w}^T\vec{x_i}+\epsilon_i$ where $\epsilon_i\sim N(0,\sigma^2)$ $\Large\Rightarrow y_i|\mathbf{x}_i \sim N(\mathbf{w}^\top\mathbf{x}_i, \sigma^2)			    \Rightarrow P(y_i|\mathbf{x}_i,\mathbf{w})=\frac{1}{\sqrt{2\pi\sigma^2}}e^{-\frac{(\mathbf{x}_i^\top\mathbf{w}-y_i)^2}{2\sigma^2}}$
![[Linear Regression Graph.png]]
Assume data is drawn from a line $\vec{w}^T\vec{x}$ through the origin
For each data point with features $x_i$ the label $y$ is drawn from a Gaussian with mean $\vec{w}^T\vec{x_i}$ and variance $\sigma^2$
**Goal:** Estimate slope $\vec{w}$ from data

## Estimating with MLE

$$\begin{aligned} \mathbf{w} &= \operatorname*{argmax}_{\mathbf{\mathbf{w}}} P(D|\mathbf{w})\\
      &=
      \operatorname*{argmax}_{\mathbf{\mathbf{w}}}
      P(y_1,\mathbf{x}_1,...,y_n,\mathbf{x}_n|\mathbf{w})\\ 
      &=
      \operatorname*{argmax}_{\mathbf{\mathbf{w}}} \prod_{i=1}^n
      P(y_i,\mathbf{x}_i|\mathbf{w}) & \\ &=
      \operatorname*{argmax}_{\mathbf{\mathbf{w}}} \prod_{i=1}^n
      P(y_i|\mathbf{x}_i,\mathbf{w})P(\mathbf{x}_i|\mathbf{w}) & \\ &=
      \operatorname*{argmax}_{\mathbf{\mathbf{w}}} \prod_{i=1}^n
      P(y_i|\mathbf{x}_i,\mathbf{w})P(\mathbf{x}_i) &
      \\ &=
      \operatorname*{argmax}_{\mathbf{\mathbf{w}}} \prod_{i=1}^n
      P(y_i|\mathbf{x}_i,\mathbf{w}) & \\ &=
      \operatorname*{argmax}_{\mathbf{\mathbf{w}}} \sum_{i=1}^n
      \log\left[P(y_i|\mathbf{x}_i,\mathbf{w})\right] & \\ &= \operatorname*{argmax}_{\mathbf{\mathbf{w}}}
      \sum_{i=1}^n \left[ \log\left(\frac{1}{\sqrt{2\pi\sigma^2}}\right) +
      \log\left(e^{-\frac{(\mathbf{x}_i^\top\mathbf{w}-y_i)^2}{2\sigma^2}}\right)\right]\\ &=
      \operatorname*{argmax}_{\mathbf{\mathbf{w}}}
      -\frac{1}{2\sigma^2}\sum_{i=1}^n (\mathbf{x}_i^\top\mathbf{w}-y_i)^2 &\\ &=
      \operatorname*{argmin}_{\mathbf{\mathbf{w}}} \frac{1}{n}\sum_{i=1}^n
      (\mathbf{x}_i^\top\mathbf{w}-y_i)^2 & \\
      \end{aligned}$$
  Steps for Reference:
  1. Definition of MLE
  2. Unpacking D
  3. Data points are i.i.d 
  4. Chain Rule of Probability
  5. $x_i$ is independent of $w$ so we only model $P(y_i|\vec{x})$
  6. $P(\vec{x_i})$ is a constant
  7. Log is a monotonic function
  8. Plug in the probability distribution
  9. First time is a constant and $log(e^z)=z$
  10. Minimize and $\dfrac{1}{n}$ makes loss interpretable

Minimizing the loss function, squared loss: $l(\mathbf{w}) =\frac{1}{n}\sum_{i=1}^n (\mathbf{x}_i^\top\mathbf{w}-y_i)^2$

Linear regression is also the Ordinary Least Squares (OLS)
- We can optimize OLS with gradient descent or Newton's method
- Optimizing with Newton's method gives us the solution: $\mathbf{w} = (\mathbf{XX^\top})^{-1}\mathbf{X}\mathbf{y}^\top$ where $\mathbf{X}=\left[\mathbf{x}_1,\dots,\mathbf{x}_n\right]$ and  $\mathbf{y}=\left[y_1,\dots,y_n\right]$

## Estimating with MAP

Assumptions: $P(\mathbf{w}) =    \frac{1}{\sqrt{2\pi\tau^2}}e^{-\frac{\mathbf{w}^\top\mathbf{w}}{2\tau^2}}$
$$\begin{align} \mathbf{w} &=
      \operatorname*{argmax}_{\mathbf{\mathbf{w}}}
      P(\mathbf{w}|y_1,\mathbf{x}_1,...,y_n,\mathbf{x}_n)\\ &=
      \operatorname*{argmax}_{\mathbf{\mathbf{w}}}\frac{P(y_1,\mathbf{x}_1,...,y_n,\mathbf{x}_n|\mathbf{w})P(\mathbf{w})}{P(y_1,\mathbf{x}_1,...,y_n,\mathbf{x}_n)}\\
      &= \operatorname*{argmax}_{\mathbf{\mathbf{w}}}P(y_1,\mathbf{x}_1,...,y_n,\mathbf{x}_n|\mathbf{w})P(\mathbf{w})\\ &=
      \operatorname*{argmax}_{\mathbf{\mathbf{w}}}\left[\prod_{i=1}^nP(y_i,\mathbf{x}_i|\mathbf{w})\right]P(\mathbf{w})\\
      &= \operatorname*{argmax}_{\mathbf{\mathbf{w}}}\left[\prod_{i=1}^nP(y_i|\mathbf{x}_i,\mathbf{w})P(\mathbf{x}_i|\mathbf{w})\right]P(\mathbf{w})\\
      &= \operatorname*{argmax}_{\mathbf{\mathbf{w}}}\left[\prod_{i=1}^nP(y_i|\mathbf{x}_i,\mathbf{w})P(\mathbf{x}_i)\right]P(\mathbf{w})\\&= \operatorname*{argmax}_{\mathbf{\mathbf{w}}} \left[\prod_{i=1}^n
      P(y_i|\mathbf{x}_i,\mathbf{w})\right]P(\mathbf{w})\\ &=
      \operatorname*{argmax}_{\mathbf{\mathbf{w}}} \sum_{i=1}^n \log
      P(y_i|\mathbf{x}_i,\mathbf{w})+ \log P(\mathbf{w})\\ &=
      \operatorname*{argmin}_{\mathbf{\mathbf{w}}} \frac{1}{2\sigma^2}\sum_{i=1}^n (\mathbf{x}_i^\top\mathbf{w}-y_i)^2 +
      \frac{1}{2\tau^2}\mathbf{w}^\top\mathbf{w}\\ &=
      \operatorname*{argmin}_{\mathbf{\mathbf{w}}} \frac{1}{n} \sum_{i=1}^n(\mathbf{x}_i^\top\mathbf{w}-y_i)^2 + \lambda|| \mathbf{w}||_2^2\tag*{\(\textrm{where:}\  \lambda=\frac{\sigma^2}{n\tau^2}\)}\\ \end{align}$$
  The final result is Ridge Regression with a closed form solution of: $\mathbf{w} = (\mathbf{X X^{\top}}+\lambda\mathbf{I})^{-1}\mathbf{X}\mathbf{y}^\top$ where $\mathbf{X}=\left[\mathbf{x}_1,\dots,\mathbf{x}_n\right]$ and  $\mathbf{y}=\left[y_1,\dots,y_n\right]$ 

## Summary

Ordinary Least Squares:
- $\operatorname*{min}_{\mathbf{\mathbf{w}}} \frac{1}{n}\sum_{i=1}^n(\mathbf{x}_i^\top\mathbf{w}-y_i)^2$
- Square loss
- No regularization
- Closed Form: $\mathbf{w} = (\mathbf{X X^\top})^{-1}\mathbf{X}        \mathbf{y}^\top$

Ridge Regression:
- $\operatorname*{min}_{\mathbf{\mathbf{w}}} \frac{1}{n}\sum_{i=1}^n(\mathbf{x}_i^\top\mathbf{w}-y_i)^2 + \lambda ||\mathbf{w}||_2^2$
- Squared loss
- $L_2$ regularization
- Closed Form: $\mathbf{w} = (\mathbf{X X^{\top}}+\lambda\mathbf{I})^{-1}\mathbf{X} \mathbf{y}^\top$
