Finds Maximum Margin seperating hyperplane

Setting: Define a linear classifer $h(x)=sign(\vec{w}^T\vec{x}+b)$ and assume a binary classification setting with labels $\{+1,1\}$

The best separting hyperplane maximizes the distance to the closest data points from both classes; the hyperplane with maximum margin

## Margin

Hyperplane: A set of points such that $\mathcal{H}=\{\vec{x}|\vec{w}^T\vec{x}+b=0\}$
Margin $\gamma$ : Distance from the hyperplane to the closest point across both classes

## Distance of a Point $\vec{x}$ to the Hyperplane $\mathcal{H}$

$\Large\| \mathbf{d} \|_2=\sqrt{\mathbf{d}^\top\mathbf{d}}=\frac{| \mathbf{w}^\top\mathbf{x}+b |}{\sqrt{\mathbf{w}^\top\mathbf{w}}}=\frac{| \mathbf{w}^\top\mathbf{x}+b |}{\| \mathbf{w} \|_{2}}$
Margin of $\mathcal{H}$ with repect to $D$: $\gamma(\mathbf{w},b)=\min_{\mathbf{x}\in D}\frac{| \mathbf{w}^\top\mathbf{x}+b |}{\| \mathbf{w} \|_{2}}$

## Max Margin Classifier 

Maximize the margin under the constraint that all data points must lie on the correct side of the hyperplane

$\underbrace{\operatorname*{argmax}_{\mathbf{w},b}\gamma(\mathbf{w},b)}_{maximize \ margin}  \textrm{ such that} \ \  \underbrace{\forall i \ y_{i}(\mathbf{w}^\top\mathbf{x}_{i}+b)\geq 0}_{separating \ hyperplane}$

We get that the new optimization problem becomes: $$\begin{align} &\min_{\mathbf{w},b}\mathbf{w}^\top\mathbf{w}\text{ such that}\ \forall i \ y_{i}(\mathbf{w}^\top \mathbf{x}_{i}+b) \geq 1 &\end{align}$$
When a seperating hyperplane exists, it has a unique solution.

Find the simplest hyperlane (smaller $\vec{w}^T\vec{w}$) such that all inputs lie at least one unit away from the hyperplane on the correct side

## Support Vectors 

**Support Vectors:** For the optimal $\vec{w},b$ pair, some training points will have tight constraint like $y_{i}(\mathbf{w}^\top \mathbf{x}_{i}+b) = 1$
- Training data that define the maximum margin of the hyperplane to the data set and determine the shape of the hyperplane
- If you move one and retrain the SVM, the hyperplane changes

## SVM With Soft Constraints

If the data is low dimensional, then sometimes there is no seperating hyperplane between the two classes. Thus there is no solution to the optimzation problems

**Solution**: Allow the constraints to be violated $$\begin{matrix}
\min_{\mathbf{w},b}\mathbf{w}^\top\mathbf{w}+C\sum_{i=1}^{n}\xi _{i} \\ 
s.t. \ \forall i \ y_{i}(\mathbf{w}^\top\mathbf{x}_{i}+b)\geq 1-\xi_i \\  \forall i \ \xi_i \geq 0        
\end{matrix}$$- If $C$ is large then the SVM is strict and tries to get the points to be on the right side of the hyperplane
- If $C$ is small, the SVM is loose and sacrifice some points for a simpler (lower $||\vec{w}||_2^2$) solution

Consider the value of $\xi_i$ when $C\neq0$. We want to minimize $\xi_i$ so we get $\xi_i=\max(1-y_{i}(\mathbf{w}^\top \mathbf{x}_{i}+b) ,0)$ as 
$$\xi_i=\left\{
\begin{array}{cc}
\ 1-y_{i}(\mathbf{w}^\top \mathbf{x}_{i}+b) & \textrm{ if \(y_{i}(\mathbf{w}^\top \mathbf{x}_{i}+b)<1\)}\\
0 & \textrm{ if \(y_{i}(\mathbf{w}^\top \mathbf{x}_{i}+b)\geq 1\)}
\end{array}
\right.$$
Thus we get $\displaystyle\min_{\mathbf{w},b}\underbrace{\mathbf{w}^\top\mathbf{w}}_{l_{2}-regularizer}+C\  \sum_{i=1}^{n}\underbrace{\max[ 1-y_{i}(\mathbf{w}^\top \mathbf{x}+b),0 ]}_{hinge-loss}$
and now we can optimize the SVM parameters $(\vec{w},b)$
