If we have a hypothesis class $\mathcal{H}$ whose set of classifiers have a large bias and the training error is high we can create a strong learner with low bias

Create ensemble classifier $H_T(\vec x) = \sum_{t = 1}^{T}\alpha_t h_t(\vec{x})$ 

In iteration $t$ we add the classifier $\alpha_th_t(\vec x)$ to the ensemble 
At test time evaluate all classifier and return the weighted sum. We add functions to our Ensemble

Let $\ell$ be a convex and differentiable loss function: 
$\ell(H)=\frac{1}{n}\sum_{i=1}^n \ell(H(\mathbf{x}_i),y_i)$

Search for weak learner that minimizes the loss: 
$$\begin{equation}
  h_{t+1} = \textrm{argmin}_{h \in \mathbb{H}}\ell(H_t + \alpha h_t).
\end{equation}$$
To find $h\in\mathcal{H}$ we use gradient descent in function space

## Gradient Descent in Functional Space

Given $H$ find a step size $\alpha$ and weak learner $h$ to minimize the loss $\ell(H+\alpha h)$

$\Large h_{t+1} = \textrm{argmin}_{h \in \mathbb{H}} \sum_{i = 1}^{n} \underbrace{\frac{\partial \ell}{\partial [H(\mathbf{x}_i)]}}_{r_i} h(x)$
We need a function $\Large\mathbb{A}(\{(\mathbf{x}_1,r_1),\dots,(\mathbf{x}_n,r_n)\})=\textrm{argmin}_{h \in \mathbb{H}} \sum_{i = 1}^{n} r_i h(\mathbf{x}_i)$
where $\mathbb{A}$ is an algorithm

## Gradient Boosted Regression Tree
- Classification or regression
- Weak learners $h\in\mathbb{H}$ are regressors 
- Step size $\alpha$ is a small constant
- Loss function: Any differentiable convex loss that decomposes over the samples $\mathcal{L}(H)=\sum_{i=1}^{n} \ell(H(\mathbf{x}_i))$

In order to use regression trees for gradient boosting we need to find a tree $h()$ that maximizes $h = \textrm{argmin}_{h \in \mathbb{H}} \sum_{i = 1}^{n} r_i  h(\mathbf{x}_i)$ where $r_i = \frac{\partial \ell}{\partial H(\mathbf{x}_i)}$

1. Assume $\sum_{i = 1}^{n} h^2(\mathbf{x}_i)$ is a constant
2. CART trees are negation closed
3. Define the negative gradient as $t_i=-r_i$
$$\textrm{argmin}_{h \in \mathbb{H}} \sum_{i = 1}^{n} r_i  h(\mathbf{x}_i)$$ $$\textrm{argmin}_{h \in \mathbb{H}}-2\sum_{i = 1}^{n} t_i h(\mathbf{x}_i)$$$$\textrm{argmin}_{h \in \mathbb{H}} \sum_{i = 1}^{n} \underbrace{t_i^2}_{\textrm{constant}} - 2t_i h(\mathbf{x}_i) + \underbrace{(h(\mathbf{x}_i))^2}_{\textrm{constant}}$$
$$\textrm{argmin}_{h \in \mathbb{H}}\sum_{i = 1}^{n}(h(\mathbf{x}_i)-t_i)^2$$
Steps:
1. AnyBoost Formulation
2. Swap $t_i$ for $-r_i$ and multiply by $2$
3. Add a constant $\sum_i t_i^2+h(\mathbf{x}_i)^2$

We can use the regression trees and feed in value $t_i$ as labels for each $x_i$. In each iteration we build a new tree for different set of tabels $t_i,\dots,t_n$

If the loss function $\ell$ is the squared loss then we can show $$t_i=-\frac{\partial \ell}{H(\mathbf{x}_i)}=y_i-H(\mathbf{x}_i)$$
The solution for our next weak learner $h()$ will be the regession tree minimizing the squared loss 

## Adaboost
- Setting: Classification
- Weak Learners: $h\in\mathbb{H}$ are binary
- Step-size: Perform line-search to obtain the best step-size $\alpha$
- Loss Function: Exponential Loss $\ell(H)=\sum_{i=1}^{n} e^{-y_i H(\mathbf{x}_i)}$

### Find the best Weak Learner
1. Compute the gradient $r_i=\frac{\partial \ell}{\partial H(\mathbf{x}_i)}=-y_i {e^{-y_i H(\mathbf{x}_i)}}$
2. Find the best next weak learner

$$\begin{align}
h(\mathbf{x}_i)&=\textrm{argmin}_{h \in \mathbb{H}}\sum_{i=1}^{n}r_ih(\mathbf{x}_i) 
&& \Big(\textrm{substitute in: } r_i=e^{-H(\mathbf{x}_i)y_i}\Big)\\
&=\textrm{argmin}_{h \in \mathbb{H}}-\sum_{i=1}^n y_i e^{-H(\mathbf{x}_i)y_i}h(\mathbf{x}_i) 
&& \Big(\textrm{substitute in: } w_i=\frac{1}{Z}e^{-H(\mathbf{x}_i)y_i}\Big)\\
&=\textrm{argmin}_{h \in \mathbb{H}}-\sum_{i=1}^{n} w_i y_i h(\mathbf{x}_i)
&& \Big(y_ih(\mathbf{x}_i)\in \{+1,-1\} \textrm{ with } h(\mathbf{x}_i)y_i=1 \iff h(\mathbf{x}_i)=y_i \Big)\\
&=\textrm{argmin}_{h \in \mathbb{H}}\sum_{i: h(\mathbf{x}_i)\neq y_i} w_i - \sum_{i: h(\mathbf{x}_i)= y_i} w_i 
&& \Big(\sum_{i: h(\mathbf{x}_i)= y_i} w_i=1-\sum_{i: h(\mathbf{x}_i)\neq y_i} w_i\Big)\\
&=\textrm{argmin}_{h \in \mathbb{H}}\sum_{i: h(\mathbf{x}_i)\neq y_i} w_i  
&& \Big(\textrm{This is the weighted classification error.}\Big)
\end{align}$$
We need a classifier that takes training data and a distribution over the training set and returns a classifier $h\in\mathbb{H}$ that reduces the weighted classification error of these training samples

## Finding the Stepsize $\alpha$

Solve the optimization problem: 
$$\begin{align}
\alpha&=\textrm{argmin}_{\alpha}\ell(H+\alpha h)\\
&=\textrm{argmin}_{\alpha} \sum_{i=1}^{n} e^{-y_i[H(\mathbf{x}_i)+\alpha h(\mathbf{x}_i)]}\\
\end{align}$$
$$\begin{align}
\sum_{i=1}^{n} y_i h(\mathbf{x}_i) e^{-\left(y_i H(\mathbf{x}_i)+\alpha y_i h(\mathbf{x}_i)\right)}  &=0 
&& \Big(   y_ih(\mathbf{x}_i)\in\{+1,-1\}\Big)\\
-\sum_{i:h(\mathbf{x}_i) y_i=1} e^{-(y_i H(\mathbf{x}_i)+\alpha \underbrace{y_i h(\mathbf{x}_i)}_\mathrm{1})} + \sum_{i:h(\mathbf{x}_i) y_i = -1} e^{-(y_i H(\mathbf{x}_i)+\alpha \underbrace{y_i h(\mathbf{x}_i)}_\mathrm{-1})}&=0 
&& \Big(w_i= \frac{1}{Z}e^{-y_iH(\mathbf{x}_i)}\Big)\\
-\sum_{i:h(\mathbf{x}_i) y_i=1} w_i e^{-\alpha} + \sum_{i:h(\mathbf{x}_i) y_i = -1} w_i e^{\alpha}&=0 
&& \Big( \epsilon=\!\!\sum_{i:h(\mathbf{x}_i)y_i=-1} \!\!w_i \Big)\\
-(1-\epsilon)e^{-\alpha}+\epsilon e^{\alpha}&=0
&& \\
e^{2 \alpha}&=\frac{1-\epsilon}{\epsilon}\\
\alpha&=\frac{1}{2}\ln \frac{1-\epsilon}{\epsilon}\\
\end{align}$$
### Renormalization
After taking a step $H_{t+1}=H_t+\alpha h$ we need to recompute the weights and renormalize 

The multiplicative update rule:$ ${w}_i\leftarrow w_i\frac{e^{-\alpha h(\mathbf{x}_i)y_i}}{2\sqrt{\epsilon(1-\epsilon)}}$

### Analysis

Weight Update:
- The weight $w_i$ is multiplied by a factor of $e^\alpha>1$ if it was classified incorrectly (increase weights) or by a factor of $e^-\alpha<1$ if it was classified correctly (decreases weights)

Normalization:
- Training Loss decreases exponentially
- After $O(log(n))$ iterations our training error must be 0

## Summary
- Boosting turns a weak classifier into a strong classifier
- During test time the computation $H(\mathbf{x})=\sum_{t=1}^T \alpha_t h_t(\mathbf{x}_t)$ can be stopped early
- Adaboost turns any weak learner into one that can classify any weighted version of the training set with below 0.5 below into a strong learner whose training error decreases exponentially and requires only $O(log(n))$ steps until it is consistent
