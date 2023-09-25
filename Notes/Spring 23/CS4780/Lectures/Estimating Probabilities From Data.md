> [!info]
> Bayes Optimal Classifier: Given $P(X,Y)$ we can predict the most likely label for $\vec{x}$. Formally, $\arg\max_y P(y|\vec{x})$

If we can estimate $P(X,Y)$ directly from the training data then we can use Bayes Optimal classifier on our estimate of $P(X,Y)$

Estimate $P(X,Y)$
- Generative Learning: Estimate $P(X,Y) = P(X|Y)P(Y)$
- Discrimative Learning: Estimate $P(Y|X)$ directly

How can we estimate probability distribution from samples?

## Maximum Likelihood Estimation (MLE)

1. Make an explicit modelign assumption about the type of distribution our data was sampled from
2. Set the parameters of this distribution so that the data is as likely as possible

> [!example] 
> **Coin Toss**
> 
>  The distribution of the observed outcomes is a binomial distribution
> 	- Binomial Distribution has two parameters: $n$ and $\theta$
> 	- Captures the distribution of n independent binary random events that have a positive outcome wih probability $\theta$
> 	- $n$: number of tosses
> 	- $\theta$: probability of heads $\rightarrow P(H) = \theta$
> 	- Binomial Distribution:  $\begin{align} P(D\mid \theta) &= \begin{pmatrix} n_H + n_T \\  n_H  \end{pmatrix} \theta^{n_H} (1 - \theta)^{n_T} \end{align}$
> 	- Computes the probability we observe $n_H$ heads $n_T$ tails if a coin was tossed $n = n_H + n_T$ times and its probability of coming up heads is $\theta$

### MLE Principle

Find $\widehat{\theta}$ to maximize the likelihood of the data $P(D;\theta)$:

$\widehat{\theta}_{MLE} = \arg\max_{\theta}P(D;\theta)$ 

1. Plug in all terms for the distribution and take log of the function
2. Compute its derivative and equate it to $0$
	- Finds an extreme point; Verify it is a maximum if the second derivative is negative

> [!example] 
> **Coin Toss Continued**
> Plug in definitions and compute the log-likelihood to the binomial distribution
>  $$\begin{align}
 \hat{\theta}_{MLE} &= \operatorname*{argmax}_{\theta} \,P(D; \theta) \\
  &= \operatorname*{argmax}_{\theta} \begin{pmatrix} n_H + n_T \\ n_H \end{pmatrix} \theta^{n_H} (1 - \theta)^{n_T} \\
&= \operatorname*{argmax}_{\theta} \,\log\begin{pmatrix} n_H + n_T \\ n_H \end{pmatrix} + n_H \cdot \log(\theta) + n_T \cdot \log(1 - \theta) \\
&= \operatorname*{argmax}_{\theta} \, n_H \cdot \log(\theta) + n_T \cdot \log(1 - \theta)
\end{align}$$ 
>Solve for $\theta$ and equate it to $0$
>$$\begin{align}
\frac{n_H}{\theta} = \frac{n_T}{1 - \theta} \Longrightarrow n_H - n_H\theta = n_T\theta \Longrightarrow \theta = \frac{n_H}{n_H + n_T}
\end{align}$$
- MLE gives an explaination for the data you observed
- If n is large and the model is correct then MLE finds the true parameters
- If n is small, MLE can overfit data, so works well when n is large
- If n is small and we do not have the correct model, then MLE is wrong

## Bayesian Way

We model $\theta$ has a random variable drawn from a distribution $P(\theta)$ 
- We specify a prior belief $P(\theta)$ defining the values we think $\theta$ is going to take on
	$P(\theta \mid D) = \frac{P(D\mid \theta) P(\theta)}{P(D)}$ where
	- $P(\theta)$: Prior distribution over the parameter $\theta$ before seeing any data
	- $P(D|\theta)$: Likelihood of the data given the paramter $\theta$ 
	- $P(\theta|D)$: Posterior distribution over the parameter $\theta$ after we observed the data

## Maximum a Posteriori Probability Estimation (MAP)


> [!info] 
> MAP Principle: Find $\hat{\theta}$ that maximizes the posterior distribution $P(\theta|D)$ $$\begin{align}
 \hat{\theta}_{MAP} &= \operatorname*{argmax}_{\theta} \,P(\theta \mid D) \\ &= \operatorname*{argmax}_{\theta} \, \log P(D \mid \theta) + \log P(\theta)\end{align}$$

> [!example]
> **Coin Toss MAP**
> $\begin{align}
 \hat{\theta}_{MAP} &= \operatorname*{argmax}_{\theta} \;P(\theta | Data) \\
&= \operatorname*{argmax}_{\theta} \; \frac{P(Data | \theta)P(\theta)}{P(Data)}\\
&= \operatorname*{argmax}_{\theta} \;\log(P(Data | \theta)) + \log(P(\theta)) \\
&= \operatorname*{argmax}_{\theta} \;n_H \cdot \log(\theta) + n_T \cdot \log(1 - \theta) + (\alpha - 1)\cdot \log(\theta) + (\beta - 1) \cdot \log(1 - \theta) \\ &= \operatorname*{argmax}_{\theta} \;(n_H + \alpha - 1) \cdot \log(\theta) + (n_T + \beta - 1) \cdot \log(1 - \theta) \\&\Longrightarrow  \hat{\theta}_{MAP} = \frac{n_H + \alpha - 1}{n_H + n_T + \beta + \alpha - 2}\end{align}$

- MAP Estimate is identical to MLE with $\alpha -1$ hallucinated heads and $\beta - 1$ hallucinated tails
- As $n \rightarrow\infty$ $\hat\theta_{MAP} \rightarrow \hat\theta_{MLE}$ as $\alpha -1$ and $\beta -1$ become irrelevant compared to large $n_H$ and $n_T$
- MAP is a great estimator if an accurate prior belief is available
- If $n$ is small and prior belief is wrong, MAP can be wrong

## True Bayesian Approach

Use posterior predictive distribution directly to make predictions about the label $Y$ of a test sample with features $X$: $$P(Y\mid D,X) = \int_{\theta}P(Y,\theta \mid D,X) d\theta = \int_{\theta} P(Y \mid \theta, D,X) P(\theta | D) d\theta$$ Generally intractable in closed form
> [!info] 
> Chain Rule $$P(A,B|C)=P(A|B,C)P(B|C)$$

## Machine Learning and Estimation

In supervised ML, we have training data $D$ and use this data to train a model, represented by its parameters $\theta$. We use the model to make predictions on a test point $x_t$

- MLE 
	- Predicts: $P(y|x_t;\theta)$
	- Learns: $\theta=\operatorname*{argmax}_\theta P(D;\theta)$
	- $\theta$ is a model parameter
- MAP
	- Predicts:  $P(y|x_t;\theta)$
	- Learns: $\theta=\operatorname*{argmax}_\theta P(\theta|D)\propto P(D \mid \theta) P(\theta)$
	- $\theta$ is a rnadom variable
- True Bayesian
	- Predicts: $P(y|x_t,D)=\int_{\theta}P(y|\theta)P(\theta|D)d\theta$

