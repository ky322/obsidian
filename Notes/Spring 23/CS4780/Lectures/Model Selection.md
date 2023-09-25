## Tuning Hyperparameters

$\vec{w}$: Model parameters which are learned
$\lambda$: Hyp that regulates bias/variance which are not learned
$$\min_{\mathbf{w}}\frac{1}{n}\sum_{i=1}^{n}\underset{Loss}{\underbrace{\ell(h_{\mathbf{w}}({\mathbf{x}_i}),y_{i})}}+\underset{Regularizer}{\underbrace{\lambda r(w)}}$$

## Overfitting and Underfitting

Underfitting: The classifier learned on the training set is not expressive enough (too simple) to account for the data provided. Both the training error and the test error will be high since the classifier does not account for relevant information in the training set

Overfitting: The classifier learned on the training set is too specific and cannot be used to accurately infer anything about unseen data. Training error decreases, but test error will increase as the classifier makes decisions based on patterns in the training set and not in the broader distribution
![[Model Selection Overfitting.png]]

## Identify the Sweet Spot

Divide data into training and validation portions and train on the training split and evaluate on the validation split

### K Fold Cross validation

Divide training data into $k$ partitions. Train on $k-1$ of them and leave one as validation set. Do this $k$ times so that every partition is left out once and average the validation error across runs.

Leave One Out Cross Validation: $k=n$; We leaeve a single data point out. Use this if our data set is small and cannot leave out many data points for evaluation

### Telescopic Search

1. Find the best order of magnitude for $\lambda$
2. Do a more fine-grained search around the best $\lambda$ found

### Grid and Random Search

Fix a set of values for each hyperparameter and try out every combination. Use if we have multiple parameters. 
**Con:** Number of settings grows exponentially with number of Hyperparameters

Random Search: Select Hyperparameters randomly within predefined intervals instead of a predefined grid

## Early Stopping

Stop optimizarion after M gradient steps even if optimization did not converge yet
