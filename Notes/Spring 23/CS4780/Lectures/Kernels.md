## Handcrafted Feature Expansion

We can make linear classifiers non-linear by applying basis function (feature transformations) on the input feature vectors
Formally: For a data vector $\vec{x}\in\mathbb{R}^d$ apply the transformation $\vec{x}\rightarrow\phi(\vec{x})$ where $\phi(\vec{x})\in\mathcal{R}^D$  
$D>>d$ because we add dimensions that capture non-linear interactions among the original features
**Pros**: Simple and our problem stays convex and well behaved (we can use gradient descent, now with higher dimensional representation)
**Cons**: $\phi(\vec{x})$ can be high dimensional

$\phi(x)$ is expressive and allows for non-linear boundaries but our dimensionality is high so our algorithm is slow $$\mathbf{x}=\begin{pmatrix}x_1\\ x_2\\ \vdots \\ x_d \end{pmatrix} \text{ and } \phi(\mathbf{x})=\begin{pmatrix}1\\ x_1\\ \vdots \\x_d \\ x_1x_2 \\ \vdots \\ x_{d-1}x_d\\ \vdots \\x_1x_2\cdots x_d \end{pmatrix}$$

## The Kernel Trick

### Gradient Descent with Squared Loss 

Kernel Trick: Learn a function in higher dimensional space withotu computing a single vector $\phi(x)$ or the full vector $w$

If we use gradient descent with any of our loss functions, the gradient is a linear combination of the input samples

#### Example
Squared Loss: $\displaystyle\ell(\mathbf{w}) = \sum_{i=1}^n (\mathbf{w}^\top  \mathbf{x}_i-y_i)^2$
The gradient descent rule with a learning rate/step size of $s>0$ or $(\alpha>0)$  updates $\vec{w}$ 
$$\Large w_{t+1} \leftarrow w_t - s(\frac{\partial \ell}{\partial \mathbf{w}})\ \textrm{ where: }
  \frac{\partial \ell}{\partial \mathbf{w}}=\sum_{i=1}^n \underbrace{2(\mathbf{w}^\top  \mathbf{x}_i-y_i)}_{\gamma_i\ :\ \textrm{function of \(\mathbf{x}_i, y_i\)}} \mathbf{x}_i = \sum_{i=1}^n\gamma_i \mathbf{x}_i$$
  We can express $w$ as a linear combination of all input vectors $\displaystyle\mathbf{w}=\sum_{i=1}^n \alpha_i {\mathbf{x}}_i$
  The update rule: $$\begin{equation}
  \alpha_i^t=\alpha_i^{t-1}-s\gamma_i^{t-1}, \textrm{ and we have } \alpha_i^t=-s\sum_{r=0}^{t-1}\gamma_i^{r}\end{equation}$$
We can perform gradient descent update rule without ever expressing $w$ directly

We can rewrite the squared loss in terms on innerproducts between training inputs: $$
\ell(\mathbf{\alpha}) = \sum_{i=1}^n\left(\sum_{j=1}^n\alpha_j\mathbf{x}_j^\top  \mathbf{x}_i-y_i\right)^2$$
During testing, we only need these coefficients to make a prediction on a test input $x_t$ and write the classifier in terms of innerproducts between the test point and training points $$
  h({\mathbf{x}}_t)=\mathbf{w}^\top {\mathbf{x}}_t=\sum_{j=1}^n\alpha_j{\mathbf{x}}_j^\top {\mathbf{x}}_t$$
The only information we need to learn a hyperplane classifier with the squareed loss is inner products between all pairs of data vectors

## Inner Product Computation

Given $\phi(\mathbf{x})=\begin{pmatrix}1\\ x_1\\ \vdots \\x_d \\ x_1x_2 \\ \vdots \\ x_{d-1}x_d\\ \vdots \\x_1x_2\cdots x_d \end{pmatrix}$ we can calculate the inner product $\phi(\vec{x})^T\phi(\vec{z})$ as $$\Large\phi(\mathbf{x})^\top \phi(\mathbf{z})=1\cdot 1+x_1z_1+x_2z_2+\cdots +x_1x_2z_1z_2+ \cdots +x_1\cdots x_dz_1\cdots z_d=\prod_{k=1}^d(1+x_kz_k)$$
The sum of $2^d$ terms becomes the product of $d$ terms. We can compute the inner product in $O(d)$ time instead of $O(2^d)$ 

Kernel Function: $\Large{\mathsf{k}(\mathbf{x}_i,\mathbf{x}_j)}=\phi(\mathbf{x}_i)^\top \phi(\mathbf{x}_j)$
With finite training set of $n$ samples, inner products are stored in a kernel matrix
Kernel Matrix: $\Large\mathsf{K}_{ij}=\phi(\mathbf{x}_i)^\top \phi(\mathbf{x}_j)$

If we store the matrix $K$ we only need to do simple inner product look up and low dimensional computations throughout the gradient descent algorithm

Final Classifier: $\displaystyle h(\mathbf{x}_t)=\sum_{j=1}^n\alpha_j\mathsf{k}(\mathbf{x}_j,\mathbf{x}_t)$
When we train in the new high dimensinoal space of $\phi(\vec{x})$ we want to compute $\gamma_i$ through kernels without computing $\phi(\vec{x}_i)$ or $w$ 
- $\Large\displaystyle\mathbf{w}=\sum_{j=1}^n\alpha_j \phi(\mathbf{x}_j)$
- $\Large\gamma_i=2(\mathbf{w}^\top \phi(\mathbf{x}_i)-y_i)$ = $\Large2(\sum_{j=1}^n \alpha_jK_{ij})-y_i)$

The gradient update in iteration $t+1$ is $\Large\alpha_i^{t+1}\leftarrow \alpha_i^t-2s(\sum_{j=1}^n \alpha_j^tK_{ij})-y_i)$

## General Kernels

- Linear: $\Large\mathsf{K}(\mathbf{x},\mathbf{z})=\mathbf{x}^\top \mathbf{z}$
- Polynominal: $\Large\mathsf{K}(\mathbf{x},\mathbf{z})=(1+\mathbf{x}^\top \mathbf{z})^d$
- Radial Basis Function (RBF) or Gaussian Kernel: $\Large\mathsf{K}(\mathbf{x},\mathbf{z})= e^\frac{-\|\mathbf{x}-\mathbf{z}\|^2}{\sigma^2}$
- Exponential Kernel: $\Large\mathsf{K}(\mathbf{x},\mathbf{z})= e^\frac{-\| \mathbf{x}-\mathbf{z}\|}{2\sigma^2}$
- Laplacian Kernel: $\Large\mathsf{K}(\mathbf{x},\mathbf{z})= e^\frac{-| \mathbf{x}-\mathbf{z}|}{\sigma}$
- Signmoid Kernel: $\Large\mathsf{K}(\mathbf{x},\mathbf{z})=\tanh(\mathbf{a}\mathbf{x}^\top  + c)$

The matrix $\mathsf{K}(\mathbf{x},\mathbf{z})$ has to correspond to real inner products after some transformation $\vec{x}\rightarrow\phi(\vec{x})$, so $\mathsf{K}$ has to be positive semi-definite

A matrix $\mathcal{A}\in\mathbb{R}^{n\times n}$ is positive and semi-definite if and only if $\forall \mathbf{q}\in\mathbb{R}^n$ $\mathbf{q}^\top A\mathbf{q}\geq 0$ 

$\mathsf{K}_{ij}=\phi(\mathbf{x}_i)^\top \phi(\mathbf{x}_j)$
$\mathsf{K}=\Phi^\top\Phi$ where $\Phi=[\phi(\mathbf{x}_1),\dots,\phi(\mathbf{x}_n)]$
$\mathsf{K}$ is positive and semi definite because $\mathbf{q}^\top\mathsf{K}\mathbf{q}=(\Phi^\top \mathbf{q})^2\geq 0$ 

If any matrix $\mathcal{A}$ is positive and semi definite it can be decomposed as $A=\Phi^\top\Phi$

