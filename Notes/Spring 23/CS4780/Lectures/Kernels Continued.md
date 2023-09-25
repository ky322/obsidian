## Well Defined Kernels

- Linear: $\Large\mathsf{K}(\mathbf{x},\mathbf{z})=\mathbf{x}^\top \mathbf{z}$
- Polynominal: $\Large\mathsf{K}(\mathbf{x},\mathbf{z})=(1+\mathbf{x}^\top \mathbf{z})^d$
- RBF: $\Large\mathsf{K}(\mathbf{x},\mathbf{z})= e^\frac{-\|\mathbf{x}-\mathbf{z}\|^2}{\sigma^2}$

New Kernels can be constructed by recursively combining rules:
1. $\mathsf{k}(\mathbf{x}, \mathbf{z})=\mathbf{x}^\top\mathbf{z}$
2.  $\mathsf{k}(\mathbf{x}, \mathbf{z})=c\mathsf{k_1}(\mathbf{x},\mathbf{z})$
3. $\mathsf{k}(\mathbf{x}, \mathbf{z})=\mathsf{k_1}(\mathbf{x},\mathbf{z})+\mathsf{k_2}(\mathbf{x},\mathbf{z})$
4. $\mathsf{k}(\mathbf{x}, \mathbf{z})=g(\mathsf{k}(\mathbf{x},\mathbf{z}))$
5. $\mathsf{k}(\mathbf{x}, \mathbf{z})=\mathsf{k_1}(\mathbf{x},\mathbf{z})\mathsf{k_2}(\mathbf{x},\mathbf{z})$
6. $\mathsf{k}(\mathbf{x}, \mathbf{z})=f(\mathbf{x})\mathsf{k_1}(\mathbf{x},\mathbf{z})f(\mathbf{z})$
7. $\mathsf{k}(\mathbf{x}, \mathbf{z})=e^{\mathsf{k_1}(\mathbf{x},\mathbf{z})}$
8. $\mathsf{k}(\mathbf{x}, \mathbf{z})=\mathbf{x}^\top \mathbf{A} \mathbf{z}$

where $k_1, k_2$ are well defined kernels $c\geq0$ and $g$ is a polynomial function with positive coefficients $f$ is any function and $\mathbf{A}\succeq 0$ is positive semi definite

Kernel being well defined is equivalent to:
1. The kernel matrix $K$ being positive semi definite
2. All eigenvalues of $K$ are non negative
3. $\exists$ real matrix $P$ such that $K = P^\top P$
4. $\forall$ real vector $\vec{x}$, $\vec{x}^\top K\vec{x}\geq0$

Prove RBF is well defined:
$$\Large\begin{aligned}
\mathsf{k}_1(\mathbf{x},\mathbf{z})&=\mathbf{x}^\top \mathbf{z} \qquad \\
\mathsf{k}_2(\mathbf{x},\mathbf{z})&=\frac{2}{\sigma^2}\mathsf{k}_1(\mathbf{x},\mathbf{z})=\frac{2}{\sigma^2}\mathbf{x}^\top \mathbf{z} \qquad\\\mathsf{k}_3(\mathbf{x},\mathbf{z})&=e^{\mathsf{k}_2(\mathbf{x},\mathbf{z})}=e^{\frac{2\mathbf{x}^\top \mathbf{z}}{\sigma^2}} \qquad\\
            \mathsf{k}_{4}(\mathbf{x},\mathbf{z})&=e^{-\frac{\mathbf{x}^\top\mathbf{x}}{\sigma^2}}
\mathsf{k}_3(\mathbf{x},\mathbf{z})
e^{-\frac{\mathbf{z}^\top\mathbf{z}}{\sigma^2}}
=e^{-\frac{\mathbf{x}^\top\mathbf{x}}{\sigma^2}}
e^{\frac{2\mathbf{x}^\top \mathbf{z}}{\sigma^2}}
e^{-\frac{\mathbf{z}^\top\mathbf{z}}{\sigma^2}}
 \qquad\\
&=e^{\frac{-\mathbf{x}^\top\mathbf{x}+2\mathbf{x}^\top\mathbf{z}-\mathbf{z}^\top\mathbf{z}}{\sigma^2}}=e^{\frac{-(\mathbf{x}-\mathbf{z})^2}{\sigma^2}}=\mathsf{k}_{RBF}(\mathbf{x},\mathbf{z})
    \end{aligned}$$
Steps:
1. Rule 1
2. Rule 2
3. Rule 7
4. Rule 6

## Kernel Machines

An algorithm can be kernelized in two steps:
1. Prove the solution lies in the span of the training points $\mathbf{w}=\sum_{i=1}^n \alpha_i \mathbf{x}_i$ for some $\alpha_i$
2. Rewrite the algorithm and classifiers so that all training or testing inputs $\vec{x_i}$ are accessed in inner products with other inputs $\mathbf{x}_i^\top \mathbf{x}_j$
3. Define a kernel function and substite $\mathsf{k}(\mathbf{x}_i,\mathbf{x}_j)$ for $\mathbf{x}_i^\top \mathbf{x}_j$

## Kernelized Linear Regression

### Recap

Ordinary Least Squares Regression (Linear Regression) minimizes the squared loss regression loss function $\min_\mathbf{w} \sum_{i=1}^{n} (\mathbf{w}^\top \mathbf{x}_i -y_i)^2$ to find the hyperplane $w$. The prediction at a test point is $h(\vec{x})=\vec{w}^\top\vec{w}$. Let $\mathbf{X}=[\mathbf{x}_1,\ldots,\mathbf{x}_n]$ and $\mathbf{y}=[y_1,\ldots,y_n]^\top$
The solution of OLS is $\mathbf{w}=(\mathbf{X}\mathbf{X}^\top)^{-1} \mathbf{X} \mathbf{y}$

### Kernelization

Express $w$ as a linear combination of the training inputs $\displaystyle\mathbf{w}=\sum_{i=1}^{n} \alpha_i\mathbf{x}_i=\mathbf{X}\vec{\alpha}$
During testing a test point is accessed only through inner products with training points $$h(\mathbf{z})=\mathbf{w}^\top \mathbf{z} = \sum_{i=1}^n\alpha_i \mathbf{x}_i^\top\mathbf{z}$$
We can kernelized the algorithm by substituting $k(\mathbf{x},\mathbf{z})$ for any inner product $\vec{x}^\top\vec{z}$  $$\begin{aligned}
             \mathbf{X}\vec{\alpha}&=\mathbf{w}= (\mathbf{X}\mathbf{X}^\top)^{-1} \mathbf{X} \mathbf{y} \\
             (\mathbf{X}^\top\mathbf{X})(\mathbf{X}^\top\mathbf{X})\vec{\alpha} &= \mathbf{X}^\top(\mathbf{X}\mathbf{X}^\top(\mathbf{X}\mathbf{X}^\top)^{-1}) \mathbf{X} \mathbf{y}\\
            \mathbf{K}^2\vec{\alpha}&= \mathbf{K} \mathbf{y} \\
             \vec{\alpha}&= \mathbf{K}^{-1} \mathbf{y}  \\
    \end{aligned}$$
Steps: 
1. Multiply from left by $\vec{X}^\top\vec{X}\vec{X}^\top$
2. Substitute $K=\vec{X}^\top\vec{X}$
3. Multiply from left by $(K^-1)^2$

Kernel Ridge Regression: $\vec{\alpha}=(\mathbf{K}+\tau^2\mathbf{I})^{-1}\mathbf{y}$
- $\tau^2>0$ increases stability
- $\tau=0$ kernel regression becomes kernelized ordinary least squares

## Testing

$\vec{w}=\vec{X}\vec{\alpha}$
The prediction of test point $\vec{z}$ becomes: $$h(\mathbf{z})=\mathbf{z}^\top \mathbf{w}
=\mathbf{z}^\top\underbrace{\mathbf{X}\vec{\alpha}}_{\mathbf{w}}
=\underbrace{\mathbf{k}_*}_{\mathbf{z}^\top\mathbf{X}}\underbrace{(\mathbf{K}+\tau^2\mathbf{I})^{-1}\mathbf{y}}_{\vec{\alpha}}=\mathbf{k}_*\vec{\alpha},$$
Closed form: $h(\mathbf{z})=\mathbf{k}_*(\mathbf{K}+\tau^2\mathbf{I})^{-1}\mathbf{y},$ where $\vec{k}_*$ is the kernel vector of the test point with the training points; the $ith$ dimension corresponding to $[\mathbf{k}_*]_{i}=\phi(\mathbf{z})^\top\phi(\mathbf{x}_i)$ the inner product between the test point $\vec{z}$ with the training point $\vec{x}_i$ after mapping into the feature space through $\phi$

## Kernel SVM

The primal SVM: $$\begin{aligned}
       &\min_{\mathbf{w},b}\mathbf{w}^\top\mathbf{w}+C \sum_{i=1}^{n} \xi_i \\
  \text{s.t. }\forall i, &\quad y_i(\mathbf{w}^\top\mathbf{x}_i +b) \geq 1 - \xi_i\\
             &\quad  \xi_i \geq 0
\end{aligned}$$
Dual SVM: $$\begin{aligned}
             &\min_{\alpha_1,\cdots,\alpha_n}\frac{1}{2} \sum_{i,j}\alpha_i \alpha_j y_i y_j K_{ij} - \sum_{i=1}^{n}\alpha_i  \\
       \text{s.t.}  &\quad 0 \leq \alpha_i \leq C\\
             &\quad \sum_{i=1}^{n} \alpha_i y_i = 0
\end{aligned}$$ where $\mathbf{w}=\sum_{i=1}^n \alpha_i y_i\phi(\mathbf{x}_i)$ so $$\begin{equation}
h(\mathbf{x})=\textrm{sign}\left(\sum_{i=1}^n \alpha_i y_i k(\mathbf{x}_i,\mathbf{x})+b\right)
\end{equation}$$
## Support vectors

In primal formulation only support vectors satisfy the constraint with equality $$y_i(\mathbf{w}^\top \phi(x_i)+b)=1$$
In dual theses same training inputs can be idenified as the dual values satisfy $\alpha_i>0$ as other training inputs have $\alpha=0$

At test time we only compute the sum in $h(\vec{x})$ over the support vectors and all inputs $\vec{x_i}$ with $\alpha_i=0$ can be ignored after training

## Recovering $b$

In the dual version $b$ is no longer part of the optimization but we need it to classify

In dual, support vectors are those with $\alpha_i>0$ so we can solve for $b$
$$\begin{aligned}
y_i(\mathbf{w}^\top \phi(x_i)+b)&=1\\
y_i\left(\sum_{j}y_j\alpha_jk(\mathbf{x}_j,\mathbf{x}_i)+b\right)&=1\\
y_i-\sum_{j}y_j\alpha_jk(\mathbf{x}_j,\mathbf{x}_i)&=b\\
\end{aligned}$$

## Kernel SVM Smart Nearest Neighbor

For a binary classification problem we can write the decision function for a test point $\vec{z}$ as $$h(\mathbf{z})=\textrm{sign}\left(\sum_{i=1}^n y_i \delta^{nn}(\mathbf{x}_i,\mathbf{z})\right)$$
where $\delta^{nn}(\mathbf{z},\mathbf{x}_i)\in\{0,1\}$ and  $\delta^{nn}(\mathbf{z},\mathbf{x}_i)=1$ only if $x_i$ is one of the $k$ nearest neighbors of test point $\vec{z}$

