Multi-layer Perceptrons and deep nets

We can make linear classifiers non linear: $w^T+b \rightarrow w^T \Phi (x) + b$
Kernelization $\Phi(x)$ makes inner products tractable
Neural Networks learns $\Phi$
Each $h_i(x)$ is a linear classifier and learns how level problems that are similar and their output is the input to the main linear classifier

## Learning 

Learn parameters of $\phi$ and then do gradient descent

We can intorudce multiple layers and increase complexity 
$\phi(x)=C\circ(B\circ(Ax+\vec{a})+\vec{b})+\vec{c}$

- The first layer learns linear functions
- The second layer combines these to multiple non linear functions 
- The third layer combines multiple non linear functions to learn more complex non-linear functions

## Forward Propagation

Back Propagation: Loss function for a single example 
For the entire training a set average over all the training points: 
$$L(\vec{x}, \vec{y}) = \frac{1}{2}(H(\vec{x}) - \vec{y})^2$$
where $H(\vec{x})=\vec{z}$ and $z_i = g(\alpha_i)$ so 
$$L = \frac{1}{2}(\vec{z} - \vec{y})^2$$
$$f'(\alpha'_j) \sum_i \delta_i W_{ij} = \vec{f'}(\vec{\alpha'}) \circ (W^T\delta)$$
## Transition functions

![[NN Graph.png]]

## Overfitting 
Neural Networks learn about of parameters and are prone to overfitting. Use Regularizers

1. Weight Decay: Use $l_2$ regularization on all weights
2. Dropout: For each input randomly remove each hidden node with probability $p$. These nodes stay removed during the backprop pass but are included for the next input

## Avoidance of Local Minima

1. Use momentum $\triangledown w_t = \Delta w_t + \mu \triangledown w_{t-1}$ where $w = w- \alpha \triangledown w_t$
	- Use some portion of the previous gradient to keep pushing out small local minima
2. Initalize weights
3. Use ReLu instead of sigmoid or tanh

## Tips and Tricks

- Rescale data so that features are within $[0,1]$
- Lower learning rate
- Use mini batch
- For image use convolution neural network