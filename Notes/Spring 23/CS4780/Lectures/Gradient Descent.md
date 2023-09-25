**Goal**: Minimize a convex, continous and differentiable loss function $\ell(w)$

## Taylor Expansion

If we have a small norm $||\vec{s}||_2$ ($\vec{w}+\vec{s}$ is close to $\vec{w}$) we can approximate $\ell(\vec{w}+\vec{s})$ with its first $$\ell(\vec{w}+\vec{s})\approx\ell(\vec{w})+g(\vec{w})^T\vec{s}$$ where $g(\vec{w})=\nabla\ell(\vec{w})$ is the gradient and second derivative $$\ell(\vec{w}+\vec{s})\approx\ell(\vec{w})+g(\vec{w})^T\vec{s}+\dfrac{1}{2}\vec{s}^TH(\vec{w})\vec{s}$$ where $H(\vec{w})=\nabla^2\ell(\vec{w})$ is the Hessian of $\ell$ 

## Gradient Descent Approximation 

Assume the function $\ell$ around $\vec{w}$ is linear and behaves like $\ell(\vec{w})+g(\vec{w})^T\vec{s}$ 
**Goal**: Find a vector $s$ that minimizes the function

In steepest descent we set $\vec{s} = -\alpha (\vec{w})$ for some $\alpha > 0$

Prove $\ell(\mathbf{w}+\mathbf{s})<\ell(\mathbf{w})$
$$\underset{after\ one\ update}{\underbrace{\ell(\mathbf{w} + (-\alpha g(\mathbf{w}))}} \approx \ell(\mathbf{w}) - \underset{>0}{\underbrace{\alpha\overset{>0}{\overbrace{ g(\mathbf{w})^T g(\mathbf{w})}}}} < \underset{before}{\underbrace{\ell(\mathbf{w})}}$$
**Learning Rate**
- If it is sufficiently small will gradient descent converge
- If it is too large, algorithm will diverge
- Safe option: Set $\alpha = \dfrac{t_o}{t}$

## Adagrad

Set the step-size adaptively for every feature
**Adagrad**: Keeps an average of the sqaured gradient magnitude and sets a small $\alpha$ for features with large gradients and large $\alpha$ for small gradients
- Setting different learning rates for different features is important if they are of different scale or vary in frequency 

## Newton's Method: Second Order approximation

Assumes loss $\ell$ is twice differentiable and uses the approximation with Hessian
**Hessian Matrix**: Second order partial derivatives 
$\ell$ is convex so it is always a symmetric square matrix and positive semi-definite
$\ell(\vec{w}+\vec{s})\approx\ell(\vec{w})+g(\vec{w})^T\vec{s}+\dfrac{1}{2}\vec{s}^TH(\vec{w})\vec{s}$ describes a convex parabola

Find its minimum by solving the optimization problem:
$$argmin_s\ell(\vec{w})+g(\vec{w})^T\vec{s}+\dfrac{1}{2}\vec{s}^TH(\vec{w})\vec{s}$$
Take the first derivative with respect to $\vec{s}$, equate it to $0$ and solve for $\vec{s}$ $$\begin{align}
g(\mathbf{w}) + H(\mathbf{w})\mathbf{s}&=0\\
\Rightarrow \mathbf{s}&= -[H(\mathbf{w})]^{-1}g(\mathbf{w})
\end{align}$$
- $\vec{s}$ converges fast if the approximation is accurate and the step is small
- $\vec{s}$ diverges if function is flat
	- The second derivative is close to $0$ and the inverse is large leading to large steps
- There is no step size that guarantees that all steps are small and local

## Best Practices

1. Matrix $H(\vec{w})$ scales $d\times d$ and is expensive to compute, so a good approximation is to only compute its diagonal entries and multiply the update with a small step size. 
	- This is a hybrid between Newton's method and gradient decent where we weight the step-size for each dimension by the inverse Hessian
2. Start with gradient descent to avoid divergence of Newton's method and finsish the optimization Newton's method.
	- The second order approximation from Newton's method is more likely to be appropriate near the optimum

Given three plots that show a comparison of Newton's method and Gradient descent
- Gradient descent always converges after over 100 iterations from all initial starting points
- If it converges, Newton's method is faster but it can diverge
- In the hybrid approach of taking 6 gradient descent steps and then switched to Newton's method converges in 10 updates