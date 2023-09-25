## Assumptions

1. Binary Classification 
	- Example: $y_i\in\{-1, +1\}$
2. Data is linearly seperable

## Classifier

$\Large h(\vec{x_i})= sign(\vec{w}^T\vec{x_i}+b)$
Bias term b: Without this the hyperplane $\vec{w}$ defines always has to go through the origin
We absorb b into the feature vector $\vec{w}$ so $x_i \rightarrow \begin{bmatrix} \vec{x_i} \cr 1 \end{bmatrix}\vec{w} \rightarrow \begin{bmatrix} \vec{w} \cr b \end{bmatrix}$ 
Verify: $\begin{bmatrix} \vec{x_i} \cr 1 \end{bmatrix}^T \begin{bmatrix} \vec{w} \cr b \end{bmatrix} = \vec{w}^T\vec{x_i}+b$
Simplify $h(\vec{x_i})$ to $\Large\displaystyle h(\vec{x_i})=sign(\vec{w}^T\vec{x})$

$y_i(\mathbf{w}^T \mathbf{x}_i) > 0 \Longleftrightarrow \mathbf{x}_i$ is classified correctly

## Geometric Intuition

![[Perceptron Geo.png]]

## Perceptron Convergence

If the data set is linearly seperable then the Perceptron will find a separating hyperplane in a finite number of updates

![[Perceptron Unit Circle.png]]

- All inputs $\vec{x_i}$ live within the unit sphere
- There exists a seperating hyperplane defined by $w^*$ where $||\vec{w}||^* =1$ 
	- $w^*$ lies on the unit sphere
- $\gamma$ is the distance from the hyperplane to the closest data point

> [!info] 
> If all of above holds, then the Perceptron makes at most $\dfrac{1}{\gamma^2}$ mistakes

