Empirical Risk Minimization: 
- Loss function $\ell$: Continous function that penalizes training error 
- Regularizer $\mathcal{r}$: Continous function that penalizes classifier complexity
$$\min_{\mathbf{w}}\frac{1}{n}\sum_{i=1}^{n}\underset{Loss}{\underbrace{\ell(h_{\mathbf{w}}({\mathbf{x}_i}),y_{i})}}+\underset{Regularizer}{\underbrace{\lambda r(w)}}$$
## Common Binary Classification Loss Functions

Assume $y_i\in\{+1,-1\}$

![[Empirical Loss.png]]

- As $z\rightarrow\neg\infty$ the log loss and the hinge loss become increasingly parallel
- The exponential loss and the hinge loss are both upper bounds of the zero-one loss

## Common Regression Loss Functions

Regression algorithm, where a prediction can lie anywhere on a real number line![[Empirical Regression.png]]

## Regularizers

Changes the formulation fo the optimization problem from an unconstrainted to constraint formulation $$\begin{equation}
\min_{\mathbf{w},b} \sum_{i=1}^n\ell(h_\mathbf{w}(\mathbf{x}),y_i)+\lambda r(\mathbf{w}) 
\Leftrightarrow 
\min_{\mathbf{w},b} \sum_{i=1}^n\ell(h_\mathbf{w}(\mathbf{x}),y_i) \textrm { subject to: } r(\mathbf{w})\leq B
\end{equation}$$
![[Empirical Reg.png]]

## Famous Cases

[Screenshot]
- Ridge Regression is very fast and can be solved in closed form if the data isn't too high dimensional
- PCA and OLS minimizes square loss, but PCA looks at perpendicular loss