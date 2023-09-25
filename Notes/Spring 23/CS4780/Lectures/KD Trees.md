k-NN Time Complexity in $d$ dimensional space
- Adding one more data point is $O(d)$
- If $n$ is the number of data points we trained on training is $O(dn)$
	- In testing, we need to compute the distance between our new data point and all of the data points we trained on
- Classifying one test input is $O(dn)$

We want the best accuracy we can so we want our training data to be large $n>>0$ but this will become a bottleneck during test time

## k-Dimensional Trees

KD-Trees partition the feature space. We want to discard data points immediately because their partition is further away that our $k$ closest neighbors. 

Partition 
1. Divide data into two halves, along one feature
2. For each training input remember the half it lies in 

Let's consider the one neighbor case:
1. Identify which side the test point lies in 
2. Find the nearest neighbors $x_{NN}^R$ of $x_y$ in the same side
3. Compute the distance between $x_y$ and the dividing wall $d_w$. If $d_w>d(x_t,x_{NN}^R)$ we are done and have a 2x speedup
If the distance to the partition is larger than the distance to our closest neighrbor, none of the data points inside that partition can be closer. We can avoid computing the distance to any of the points in the entire partition.

If $d_w$ is larger than the distance to the current best candidate point for the nearest neighbor, we can discard $x$ as a candidate

## KD-Tree Data Structure

Tree Construction:
1. Split data recursively in half on one feature
2. Rotate through features 
	- Pick feature with maximum variance
Pro: 
- Exact 
- Easy to build
Cons:
- Curse of Dimensionality makes KD-Trees ineffective for higher number of dimensions 
- All splits are axis aligned
Approximation:
- Limit search to $m$ leaves only

## Ball Trees 

Instead of the boxes from KD-Trees, use hyperspheres (balls)

If the distance to the ball $d_b$ is larger than the distance to the currently closest neighbor, we can ignore the ball and all points within

Using a ball structure allows us to partition the data along an underlying manifold that our points are on instead of repeatedly dissecting the feature space

Ball Tree Construction
Input: Set $S$, $n=|S|, k$

## Ball-Tree Use

Same as KD-Trees. Slower than KD-Trees in low dimensions ($d\leq3$) but faster in higher dimension. Both are affected by the curse of dimensionality but Ball trees still work if data exhibits local structure (lies on a low-dimensional manifold)

## Summary
- kNN is slow during testing because it does unnecessary work 
- KD-Trees partition the feature space so we can rule our whole partitions that are further away than our closest $k$ neighbors. The splits are axis aligned which does not extend well to higher dimensions 
- Ball-Trees partition the manifold the points are on instead of the whole space., which performs  better in higher dimensions