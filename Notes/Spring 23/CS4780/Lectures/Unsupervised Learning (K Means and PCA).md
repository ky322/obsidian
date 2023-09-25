We have features $x_i, \dots, x_n (x_i \in \mathbb{R})$ and no labels (no $y_i$)
We are interested in uncovering structures in the feature vectors themselves
A key feature of unsupervised learning problem is that the strcutre we find is tied to the algorithm we choose
1. k-Means Clustering: Determines similar groups of feature vectors based on euclidean distances
2. Principal Component Analysis: 
	1. Detemine if the collection of feature vectors lie in a lower dimensional space than their latent dimesnion $d$
	2. A small set of synthetic features that fcan be used to describe variablity in the data

## K-Means Clustering
Given a set of $n$ data points (feature vectors) $x_i, \dots, x_n (x_i \in \mathbb{R})$
**Goal**: Partition data into $k$ groups where each group contains similar objects as defined by their euclidean distances

## k-Means Objective Formally

Let $k$ subsets $C_1, \dots, C_K$ with $C_i \subseteq \{1,\dots,n\}$ be the k clusters of points
- If $x_i$ is assigned to cluster $j$ then $i \in C_j$
These subsets define a proper partition of the data so:
- $\cup_i C_i = \{1,\dots, n\}$ (Every data points get assigned to a cluster)
- $C_i \cap C_{i'} = \emptyset$ for $i \neq i'$ (Clusters do not overlap)

**Goal**: Find clusters where data points within each cluster are tightly grouped (low variablity)

> [!info]
> $||x||_2^2 = x^Tx$ so $||x_i - x_j||_2$ is the euclidean distance between the vectors $x_i$ and $x_j$

For any cluster assignment: $$Z(\mathcal{C}_{1},\ldots,\mathcal{C}_{k}) = \sum_{\ell=1}^{k}\frac{1}{2\lvert\mathcal{C}_{\ell}\rvert} \sum_{i,j\in\mathcal{C}_{\ell}} \|x_{i} - x_{j}\|^{2}_ {2}$$
The smaller the Z the better the clustering; We want to pick a clustering that minimizes the pairwise squared distances within each cluster
In terms of the centriod of each cluster: $$Z(\mathcal{C}_{1},\ldots,\mathcal{C}_{k}) = \sum_{\ell=1}^{k}\sum_{i\in\mathcal{C}_{\ell}} \|x_{i} - \mu_{\ell}\|^{2}_ {2},$$ where $\mu_{\ell} = \frac{1}{\lvert\mathcal{C}_{\ell}\rvert} \sum_{i\in\mathcal{C}_{\ell}} x_i$ is the mean/centroid of the points in cluster $\mathcal{l}$
Goal: $\Large\min_{\mathcal{C}_{1},\ldots,\mathcal{C}_{k}} Z(\mathcal{C}_{1},\ldots,\mathcal{C}_{k})$

## Algorithm For k-Means

Given some intital clustering, we iteratively update the cluster asssignments that yields a better clustering

**Lloyd's Algorithm:**
Input: data $\{x_i\}_{i=1}^n$ and $k$
Initialize $C_1,\dots, C_k$
While not converge:
	1. Compute $\mu_{\ell} = \frac{1}{\lvert\mathcal{C}_{\ell}\rvert} \sum_{i\in\mathcal{C}_{\ell}} x_i$ for $\ell = 1, \dots, k$
	2. Update $C_1,\dots, C_k$ by assigning each data point $x_i$ to the cluster whos centroid $\mu_\ell$ is closest to
	3. If the cluster assignments didn't change then we converged
Return: Cluster assignments $C_1,\dots, C_k$

> [!summary] 
 > At each step we compute the centroid for each cluster and then reassign points to clusters based on which centroid they are closest to

Lloyd's algorithm takes $O(ndk)$ per iteration
- It's efficiency is dependent on how many iterations it takes to converges
- Lloyd's does not always solve the optimization problem

## How to Initialize and Choose Number of Clusters

Two choices to make that can have a strong influence on output
1. **Number of Clusters ($k$):** Look for a “knee” in the objective function
2. **Initial Cluster Assignment:** Lloyd's only finds a local optima so different initalization can converge to different solutions. For each $k$ try random inital clustering assignments and run the algorithm from each initial clustering and take the output over those runs that yielded the smallest $Z_k \equiv Z(\mathcal{C}_{1},\ldots,\mathcal{C}_{k})$ (the computed objective value after we run Lloyd’s algorithm)

## Decision Boundaries

This structure can be described based on how cluster centroids partition $\mathbb{R}^d$ when the cluster assignments are made.
- Given two cluster centroids $\mu_\ell$ and $\mu_{\ell'}$ the set of points equidistant from the two centroids defined as $\{x\in\mathbb{R}^d \;\vert\; \|x-\mu_{\ell}\|_ 2 =\|x-\mu_{\ell'}\|_ 2\}$ is a line
- Given a set of cluster centroids $\mu_i,\ldots,\mu_k$ they partition the space into $k$ domains whose boundaries are linear

## Principal Component Analysis

- k-means clustering partition the data into homogenous subgroups
- PCA finds low dimensional structure in the data set $\{x\}_{i=1}^n$ where $x_i \in \mathbb{R}^d$
1. PCA finds a low dimensional representation of the data that captures most of the variablity
	- Computing the composite featrures (linear combinations of entries in each $x_i$) that explains most of the variablity in the data
2. PCA provides low dimensional approximation to the data that is the best possible give the dimension

## Centering the Data

If data has a large mean $\mu = \frac{1}{n}\sum_i x_i$ is far from zero, then the best approximation of each data point is $\mu$, but most of the interesting behavior in the data may occur in a different direction
Thus, we center our data before applying PCA: $\Large\hat{x}_ i = x_i - \mu$ where $\Large\mu = \frac{1}{n}\sum_i x_i$
We work now with the centered feature vectors $\Large\{\hat{x}_ i\}_ {i=1}^n$

## Maximizing the Variance

1. Find a small set of composite features that capture most of the variablity in the data
	1. Find a single composite feature that captures as much of the variablity in the data set.
	- Mathematically: Find a vector $\phi\in\mathbb{R}^d$ such that the sample variance of the scalars $z_i = \phi^T\hat{x}_ i$ is as large as possible and $\|\phi\|_ 2 = 1$
	- First Principal Component of a Data Set: The vector $\phi\in\mathbb{R}^d$ that solves $\Large\max_{\|\phi\|_ 2=1} \frac{1}{n}\sum_{i=1}^n(\phi^T\hat{x}_ i)^2$
2. Optimization:
	- First Principal Component
		- Consider the data matrix: $\widehat{X}= \begin{bmatrix} \vert & & \vert \\ \hat{x}_ 1 & \cdots & \hat{x}_ n\\\vert & & \vert\end{bmatrix}$
		- The new problem we want $\phi\in\mathbb{R}^d$ to solve $\Large\max_{\|\phi\|_ 2 =1}\|\hat{X}^T\phi\|_ 2$ in other words $\phi$ is the unit vector that makes the matrix $\widehat{X}^T$ as large as possible
		- We can decompose $\widehat{X}$ as $\widehat{X}=U\Sigma V^T$ where $U = \begin{bmatrix} \vert & & \vert \\ u_ 1 & \cdots & u_ d\\\vert & & \vert\end{bmatrix}, \quad V = \begin{bmatrix} \vert & & \vert \\ v_ 1 & \cdots & v_ d\\\vert & & \vert\end{bmatrix}, \quad \text{and} \quad \Sigma =  \begin{bmatrix} \sigma_1 & & \\ & \ddots & \\& & \sigma_d \end{bmatrix}$ 
			- $u_i$: left singular vectors
			- $v_i$: right singular vectors
			- $\sigma_i$: singular values
			- Assuming $\sigma_1 > \sigma_2$ the solution to $\Large\max_{\|\phi\|_ 2=1} \frac{1}{n}\sum_{i=1}^n(\phi^T\hat{x}_ i)^2$ is $\phi = u_1$ and $\phi$ can be written as $\phi = \sum_{i=1}^d a_i u_i$ so $$\begin{align}
			\|\widehat{X}^T\phi\|_ 2^2 &= \|V\Sigma U^T\phi\|_ 2^2 \\
			& = \left\|\sum_{i=1}^d (\sigma_i a_i) v_i\right\|_ 2^2 \\ 
			& = \sum_{i=1}^d (\sigma_i a_i)^2\end{align}$$
		- Thus the quantity is maximized by setting $a_1=1$ and $a_i=0$ for $i \neq1$
		- The first left singular value of $\widehat{X}$ gives the first PCA of the data
	- Additional Directions
		- Look for composite features with the next most variablity
		- Look for $\psi$ such at $y_i= \psi^T\hat{x_i}$ has maximal sample variance
			- This gets the first PCA so we need to force the second PCA to be distinct from the first 
			- Solution: Force them to be orthogonal $\psi^T\phi=0$
		- The second PCA is $\psi = u_2$
		- Consider the top k principal components; the k directions in which the data varies the most
		- Principal Component $\ell$ denoted as $\phi_\ell$ and we want to find different directions so $\phi_{\ell}^T\phi_{\ell'}^{\phantom{T}} = 0$ for $\ell\neq\ell'$
			- Order them by sample variance of $\phi_{\ell}^T\hat{x}_ i$ 
			- $\phi_{\ell}^T\hat{x}_ i$ has more variablity than $\phi_{\ell'}^T\hat{x}_ i$ for $\ell<\ell'$
		- Principal Components $\ell$ of a data set $\{x_i\}_ {i=1}^n$ is denoted by $\phi_\ell$ 
			- Satisfies: $\phi_\ell = u_\ell$ where $\widehat{X}= U\Sigma V^T$ is the SVD of $\widehat{X}$

## Explaining Variablity in the Data

How does principal components explain variablity in the data?
-  By using SVD of $\widehat{X}$ we computed the sample variance for each principal component 
- The singular values reveal the sample variance of $\phi_{\ell}^T\hat{x}_ i$

PCA provides a low dimensional representation of the data

How many should we compute?

Pick $k$ such that $\phi_1,\dots,\phi_k$ captures most of the variablity in the data

Total variablity of the data: $\displaystyle\sum_{j=1}^d\sum_{i=1}^n (\hat{x}_ i (j))^2$
- Sum up the squares of all the entires in the data points

However, total variablity in the data is also encoded in the singular values of $\widehat{X}$ as $\displaystyle\sum_{j=1}^d\sum_{i=1}^n (\hat{x}_ i (j))^2 = \sum_{i=1}^d \sigma_i^2$

Also, the total variablity in the data is captured by the first $k$ principal components: $\displaystyle\sum_{i=1}^k \sigma_i^2$

The proportion of the total variance by the first $k$ principal components is $\displaystyle\frac{\displaystyle\sum_{i=1}^k \displaystyle\sigma_i^2}{\displaystyle\sum_{i=1}^d \sigma_i^2}$

We pick $k$ to explain whatever fraction of the variance we want or pick k by identifying whenever we have diminishing returns in explaining variance by adding more principal components (looking for a knee in the plot of singular values)

## Best Approximations

PCA solves a best approximation problem for our centered data $\hat{x}_i$

If we want to approximate every data point $\hat{x}$ by a point $w_i$ in a fixed $k$ dimensional subspace, which subspace should we pick to minimize $\displaystyle\sum_{i=1}^n \|\hat{x}_ i - w_i\|_ 2^2$ ?
- Find a matrix $W$ with orthonormal columns that solves: $\min_{\substack{W\in\mathbb{R}^{n\times d}\\ \\ W^TW = I}} \displaystyle\sum_{i=1}^n \|\hat{x}_ i - W(W^T\hat{x}_ i)\|_ 2^2.$
- Solution: Set columns of $W$ to be the first $k$ left singular vectors of $\widehat{X}$ or the first $k$ principal components
- If we want to project our data $\hat{x_i}$ onto a $k$ dimensional subspace thebest choice is the subspace defined by our first $k$ principal components
- Best: the subspace where the sum of the squared distances between the data points and their projections are minimized

## PCA For Visualization

We also use PCA for data visualization

If we have high dimensional data that is hard to visualize, we can see key features of the data by plotting its projection onto a few principal components

Example: if $d=2$ then corresponds to a scatter plot of $(\phi_1^T\hat{x}_ i, \phi_2^T\hat{x}_ i)$

Any key information that is orthogonal to the first few principal components will be 