# Intro
The goal in supervised learning is to mkae predictions from data
**Classifier**:  Predict the correct label of each annoted data instance

# Setup
**Training Data**: Pairs of input, $\Large(\vec{x},{y})$ where $\large\vec{x} \in R^d$ is the input instance and $y$ is the label.

The entire training data is denoted as: $$\Large D=\{(\vec{x_1},y_1),\dots,(\vec{x_n},y_n)\} \subseteq R^d \times C$$ where 

- $\Large R^d$ : d-dimensional feature space
- $\Large\vec{x}_i$ : input vector of the ith sample
- $\Large y_i$ : label of the ith sample
- $\Large C$ : label space
The data points $\Large (\vec{x_i},y_i)$ are drawn from some unknown distribution $\Large P(X,Y)$
Goal: Learn a function $\Large h$ such that for a new pair $\Large (\vec{x},y) \sim P, h(\vec{x} = y)$  with high probability
d
## Examples of Label Spaces

For label space $C$
| Binary Classification | $C = \{0, 1\}$ or $C = \{-1, +1\}$  | Spam filtering; Email is either spam (+1) or not (-1) |
| ---------- | --------- | ---------|
| Multi-Class Classification        | $C = \{1, 2, ..., K\}$ where K $\geq$ 2   |Face classification; A person can be exactly one of K identities 
| Regression      | $C = \mathbb{R}$     | Predict future temperature or the height of a person

## Examples of feature vectors

**Feature Vector** : $\Large\vec{x_i}$ 
Each one of its d dimensions is a feature describing the ith sample
- Patient Data: $\Large\vec{x_i} = (x_i^1, x_i^2, ..., x_i^d)$  where
	- $x_i^d = 0$ or $1$ may refer to patient i's gender 
	- $x_i^2$ could be the height of patient i in cm
	- $x_i^3$ can be the years
	- $d \leq 100$ 
	- Feature vector is **dense** (number of non-zero coordinates in $\vec{x_i}$ is large relative to $d$)
- Text Document in Bag of Words Format: $\Large\vec{x_i} = (x_i^1, x_i^2, ..., x_i^d)$ where $x_i^\alpha$ is the number of occurrences of the $\alpha th$ word in a dictionary in document i (term frequencies)
	- $d \sim 100,000 - 10M$ 
	- Feature vector is **sparse** ($\vec{x_i}$ consists of mainly 0s)
	- Avoid use of dictionary by using feature hashing to directly hash any string o a dimension index
- Images: Features represent pixel values $\Large\vec{x_i} = (x_i^1, x_i^2, ..., x_i^{3k})$
	- $x_i^{3j-2}, x_i^{3j-1}, x_i^{3j}$ refer to the red, green, and blue values of the $jth$ pixel in the image
	- $d \sim 100,000 - 10M$
	- Feature vector is **dense** 

## Hypothesis Class and No Free Lunch

**Hypothesis Class** : the set of possible functions

By specifying the hypothesis class, we are encoding important assumptions about the type of problem we are trying to learn

**No Free Lunch Theorem:** Every successful ML algorithm must make assumptions
-  No single ML algorithm works for evey setting

## Loss Functions

Two steps in learning a hypothesis function $h()$:
1. First, select the type of machine learning algorithm that is appropriate for the learning problem. This defines the hypothesis class $\mathcal{H}$ (the set of functions we can learn)
2. Find the best function within this class ($h \in \mathcal{H}$). This is the actual learning processand involves an optimization problem
We try to find a function $h$ within the hypothesis class that makes the fewest mistakes within our training data.

**Loss Function**: Evaluates a hypothesis $h \in \mathcal{H}$ on our training data and tells us how bad it is; The higher the loss, the worse it is

### Examples
- Zero-One Loss
	- Counts how many mistakes a hypothesis function $h$ makes on the training set
	- For every single example it suffers a loss of 1 if it is mispredicted and 0 otherwise
	- Often used to evaluate classifiers in multi-class or binary classification
	- Not useful in optimization because the function is non-differentiable and non-continuous 
	- Formally, $$\Large\mathcal{L_{0/1}(h) = \dfrac{1}{n}\sum^{n}_{i =1}\delta_{h(\vec{x_i})\neq y_i}}$$ where $\Large\delta_{h(\vec{x_i})\neq y_i} = \begin{cases}1 & \text{if } h(\vec{x_i} \neq y_i) \\ 0 & \text{Otherwise} \end{cases}$
	- Returns the error rate on this data set $D$
	- For every example that the classifier misclassifies a loss of 1 is suffered whereas correctly classified samples leade to 0 loss
- Squared Loss:
	- Typically used in regression settings
	- Iterates over all the training samples and sufferes the loss $\Large(h(\vec{x_i}) - y_i)^2$
		- By squaring:
			1. The loss suffered is nonnegative
			2. The loss suffered grows quadratically with absolute mispridcted amount
			This encourages no predictions to be far off, otherwise the penalty would be so large that a different hypothesis function is better suited. On the flipside, if a prediction is very close to being correct, the square will by tiny and little attention will be given to that example to obtain zero error.
	- If, given input $\vec{x}$, the label $y$ is probabilistic according to some distribution $P(y|\vec{x})$ then the optimal prediction to minimize the square loss is to predict the expected value: $\Large h(\vec{x}) = \mathbf{E_{P(y|\vec{x})}[y]}$
	- Formally, $$\Large\mathcal{L_sq}(h) = \dfrac{1}{n}\sum^{n}_{i=1}(h(\vec{x_i})-y_i)^2$$
- Absolute Loss:
	- Typically used in regression settings
	- Suffers the penalties $\Large|h(\vec{x_i}-y_i)|$
	- Suffered loss grows linearly with mispredictions so it is more suitable for nosiy data (when some mispredictions are unavoidable and should not dominate the loss)
	- If, given input $\vec{x}$, the label $y$ is probabilistic according to some distribution $P(y|\vec{x})$ then the optimal prediction to minimize the square loss is to predict the median value: $\Large h(\vec{x}) = MEDIAN_{P(y|\vec{x})}[y]$
	- Formally, $$\Large\mathcal{L}_{abs} = \frac{1}{n}\sum^{n}_{i=1}|h(\vec{x_i})-y_i|$$
## Generalization
Given a loss function, we then find the function $h$ that minimizes the loss: $h = argmin_{h \in \mathcal{H}}\mathcal{L}(h)$

## Train and Test Splits

To resolve overfitting we split D into three subsets: $D_{TR}$ (training data), $D_{VA}$ (validation data), and $D_{TR}$ (test data). They are split into a proportion of 80%, 10%, and 10%. Then we choose $h()$ based on $D_{TR}$ and evalutate $h()$ on $D_{TE}$

$D_{VA}$ is used to check if the $h()$ obtained from $D_{TR}$ suffers from overfitting
$h()$ needs to be validated on $D_{VA}$ and if the loss is too large $h()$ will be revised based on $D_{TR}$ and validated again on $D_{VA}$. This process continues until we get a low loss on $D_{TR}$

Trade off for different sizes of $D_{TR}$ and $D_{VA}$: Training results are better for a larger $D_{TR}$ but validation is more reliable (less noisy) for a larger $D_{VA}$

### How To Split Data

**By Time**: If data if temporally collected
**Uniformly at Random**: If and only if the data is i.i.d

The best error (testing loss) approximates the true generalization error/loss

## Conclusion

We train our classifier by minimizing thte training loss $$\Large h^*()= argmin_{h()\in\mathcal{H}}\dfrac{1}{|D_{TR}|}\sum^{}_{(\vec{x},y)\in D_{TR}}\mathcal{l}(\vec{x},y|h())$$
where $\mathcal{H}$ is he hypothesis class (the set of all possible classifiers $h()$)
We are trying to find a hypothesis $h$ that performs well on past and known data
We evaluate our classifier on the testing loss: $$\Large\epsilon_{TE} = \dfrac{1}{|D_{TE}|}\sum^{}_{(\vec{x}, y) \in D_{TE}}l(\vec{x}, y|h^*())$$
If the samples are drawn i.i.d from the same distribution $\mathcal{P}$ then the testing loss is an unbiased estimator of the true generalization loss: $$\Large\epsilon = \mathbb{E}_{(\vec{x},y) \sim \mathcal{P}}[l(\vec{x}, y|h^*())]$$
**Weak Law of Large Numbers**: The empirical average of data drawn from a distribution converges to its mean so $\epsilon_{TE} \rightarrow\epsilon$ as $|D_{TE}| \rightarrow +\infty$

**No Free Lunch**: Every ML algorithm has to make assumptions on which hypothesis class $\mathcal{H}$ choosen. The choice depends on the data and enocdes your assumptions about the data set/ distribution $\mathcal{P}$

