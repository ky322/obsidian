
## The K NN Algorithm
**Assumption**: Similar inputs have similar outputs
**Classification Rule**: For a test input $\vec{x}$ assign the most common label amongst its k most similar training inputs

### Formal Definition of k-NN
- Test point: $\vec{x}$
- $S_\vec{x}$: the set of the k nearest neighbors of $\vec{x}$
- Every point in D but not in $S_\vec{x}$ is at least as far away from $\vec{x}$ as the furthest point in $S_\vec{x}$
- $h()$: classifier; the function returning the most common label in $S_\vec{x}$:  $$\Large h(\vec{x})=mode(\{y^":(\vec{x^"},y^")\in S_\vec{x}\})$$
## Distance Function to Use 
- The better the distance metric reflects label similarity, the better the classified will be
- **Minkowski Distance**: $\Large dist(\vec{x}, \vec{z})=(\sum^{d}_{r=1}|x_r-z_r|^p)^{\frac{1}{p}}$

## Bayes Optimal Classifier

Assume you knew $P(y|\vec{x})$ then we predict the most likely label
- Bayes Optimal Classifier predicts: $y^*=h_{opt}(\vec{x})= argmax_y P(y|\vec{x})$
- Bayes Optimal Classifier is as good as it gets, but is always wrong if a sample does not have the most likely label
- It provides a highly informative lower bound of the error rate
- With the same feature representation no classifier can obtain a lower error

### Best Constant Predictor

- **Upper Bound on Error**: A classifier that we will always beat
- **Constant Classifier**: Predicts the same constant independent of any feature vectors
- Best Constant
	- Classification: Most common label in the training set
	- Regression: Constant that minimizes the loss on the training set 
		- For the square loss: Average label
		- For the absolute loss: Median label
- You should always show that your classifier performs significantly better on the test set than the best constant

## 1-NN Convergence

As $n \rightarrow \infty$ the 1-NN error is no more than twice the error of the Bayes Optimal classifier
**Reminder:** Bayes Optimal Classifier is the best possible classifer

## Curse of Dimensionality

### Distances Between points

The kNN classifier makes the assumption that similar points share similar labels. However, in high dimensional spasces, points that are drawn from a probability distribution tend to never be close together.

As d $>>$ 0, the entire space is needed to find 10-NN which breaks down the k-NN assumption because the k-NN are not closer and more similar than any other data points in the training set

### Distances to Hyperplanes

For a 2D plot: Pairwise distances grow in high dimensions since for $d=2$ distance between two points is $\sqrt{\Delta x^2 + \Delta y^2}$ and for a third dimension the distance is $\sqrt{\Delta x^2 + \Delta y^2 + \Delta z^2}$

For a 3D plot: Distance to hyperplane remains unchanged as the third dimension is added. The normal of the hyperplane is orthogonal to new dimensions

In $d$ dimensions, $d-1$ dimensions will be orthogonal to the normal of any hyperplane

As distances between pairwise points become very large in high dimensional spaces, distances to hyperplanes become compartively tiny

Movement in those dimensions cannot increase or decrease the distance to the hyperplane; the points will just shift around and remain at the same distance

## Data with Low Dimensional Structure

Data may lie in low dimensional subspaces such as natural Images
Instrinsically low dimensional data set: Human faces; An image of a human face needs $18M$ but a person can describe this person with less than 50 attributes along which faces vary

## k-NN Summary
- Simple and effective classifier if distances reflect a sementically meaningful notion of the dissimilarity 
- As $n \rightarrow \infty$ k-NN is very accurate but slow
- As $d>>0$ points drawn from a probability distribution stop being similar to each other and the k-NN assumption breaks down
