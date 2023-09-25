## Motivation 

- Learn non-linear decision boundaries
- Can handle multi-class problems
- kNN uses a lot of storage 
- The more training data we have the slower it becomes during testing since we need to compute distances to all training inputs
- We need a good distance metric
- Assume similar inputs have similar neighbors
	- Implies data points of various classes appear in clusters of homogenous class assignments

Decision Trees exploit the fact that if we know a test points falls into a cluster of one million points with a positive label thn the neighbors are positive even before computing the distance to each of the million distances

We do not store the training daa but use the data to build a tree structure that recursively divides the space into regions with similar labels.

The root node of the tree represents the entire data set. Then we split the set in half along one dimension by a threshold $t$.
- All points that have a feature value $\geq t$ fall into the right child node
- All other have left child node
- $t$ and the dimension are chosen so that the child nodes are purer in terms of class membership
- Ideally all positive points fall into one child node and all negative points in the other
	- If so the trew is done, else the leaf nodes are split again until leaves are pure (data points contain the same label or cannot be split any further)
Advantages Over Nearest Neighbor Algorithm:
1. Once tree is constructed, the training data does not need to be stored 
	- Store label of all points
2. Fast during test time
	- Test inputs need to traverse down the tree to a leaf
	- Prediction is the majority label of the leaf
3. Requires no metric because the splits are based on feature thresholds and not distances

Goal: Build a tree that is:
1. Maximally compact
2. Only has pure leaves

It is possible to find a consistent tree if and only if no two input vectors have identical features but different labels

Finding a minimum size tree is NP-Hard
Soution: We can approximate it by splitting the data to minimize an impurity function that measures label purity amongst the children

## Impurity Function

Data: $S=\left \{ \left ( \mathbf{x}_1,y_1 \right ),\dots,\left ( \mathbf{x}_n,y_n \right ) \right \}, y_i\in\left \{ 1,\dots,c \right \}$ where $c$ is the number of classes

### Gini Impurity

Let $S_k\subseteq S$ where $S_k=\left \{ \left ( \mathbf{x},y \right )\in S:y=k \right \}$ (all inputs with labels $k$) 
$S=S_1\cup \dots \cup S_c$

$p_k=\frac{\left | S_k \right |}{\left | S \right |}\leftarrow \textrm{fraction of inputs in } S \textrm{ with label } k$

$G(S)=\sum_{k=1}^{c}p_k(1-p_k)$

Gini Impurity of a Tree: $$G^T(S)=\frac{\left | S_L \right |}{\left | S \right |}G^T(S_L)+\frac{\left | S_R \right |}{\left | S \right |}G^T(S_R)$$ where: 
- $\left ( S=S_L\cup S_R \right )$
- $S_L\cap S_R=\varnothing$
- $\frac{\left | S_L \right |}{\left | S \right |}\leftarrow \textrm{fraction of inputs in left substree}$
- $\frac{\left | S_R \right |}{\left | S \right |}\leftarrow \textrm{fraction of inputs in right substree}$

### Entropy

Impurity is how close are to uniform. KL-Divergence computes closeness $$KL(p||q)=\sum_{k=1}^{c}p_k\log\left(\frac{p_k}{q_k}\right)\geq 0 \leftarrow \textrm{\(KL\)-Divergence}$$ $$=\sum_{k}p_k\log(p_k)-p_k\log(q_k)\textrm{ where }q_k=\frac{1}{c}$$
$$=\sum_{k}p_k\log(p_k)+p_k\log(c)$$
$$=\sum_{k}p_k\log(p_k)+\log(c)\sum_{k}p_k \textrm{ where  } \log(c)\leftarrow\textrm{constant}, \sum_{k}p_k=1$$
$$\max_{p}KL(p||q)=\max_{p}\sum_{k}p_k\log(p_k)$$
$$=\min_{p}-\sum_{k}p_k\log(p_k)$$
$$=\min_{p}H(s) \leftarrow\textrm{Entropy}$$
Entropy over Tree: $$H(S)=p^LH(S^L)+p^RH(S^R)$$ where $p^L=\frac{|S^L|}{|S|}, p^R=\frac{|S^R|}{|S|}$

### ID3 Algorithm

## Regression Trees

Assume labels are continous: $y_i\in\mathbb{R}$
Impurity: Squared Loss $$L(S)=\frac{1}{|S|}\sum_{(x,y)\in S}(y-\bar{y}_S)^2 \leftarrow\textrm{Average squared difference from average label}$$ where $\textrm{where }\bar{y}_S=\frac{1}{|S|}\sum_{(x,y)\in S}y\leftarrow\textrm{Average label}$

At leaves we predict $\bar{y}_s$ 
Finding the best split only costs $O(nlogn)$

### CART Summary 
- Light weight classifiers
- Fast during testing 

## Parametric and Non Parametric Algorithms

Parametric Algorithm: Constant set of parameters which is independent of the number of training samples.
- The amount of space needed to store the trained classifier
- Perceptron or Logisitic regression
	- Parameters: $\vec{w}$ and $b$ which define the separating hyperplane
	- The dimension of $w$ depends on the dimension of the training data but not on the number of training samples in training 
Non Parametric Algorithm: The number of parameters scales as a function of the training samples 
- kNN: During training we store the entire training data so parameters we learn are identical to the training set
- Number of parameters (storage needed) grows linearly with the training set size

- If the kernel is linear the algorithm is parametric
- Kernel-SVM with RBF kernel is non parametric
- Decision Trees are non-parametric if trained to full depth as the depth of a decision tree scales as a function of the training data
	- If we limit the depth by a maximum value they become parametric

