The Bias Variance Decomposition:
$$\begin{equation*}
    \underbrace{\mathbb{E}[(h_D(x) - y)^2]}_\mathrm{Error} = \underbrace{\mathbb{E}[(h_D(x)-\bar{h}(x))^2]}_\mathrm{Variance} + \underbrace{\mathbb{E}[(\bar{h}(x)-\bar{y}(x))^2]}_\mathrm{Bias} + \underbrace{\mathbb{E}[(\bar{y}(x)-y(x))^2]}_\mathrm{Noise}
\end{equation*}$$
Goal: Reduce the variance term so we want $h_D\rightarrow\bar{h}$

## Weak Law of Large Numbers 

For i.i.d random variables $x_i$ with mean $\bar{x}$ $$\frac{1}{m}\sum_{i = 1}^{m}x_i \rightarrow \bar{x} \textrm{ as }  m\rightarrow \infty$$
Then we can apply this to classifiers. Assume we have $m$ training sets $D_1, D_2, ..., D_n$ drawn from $P^n$ $$\hat{h} = \frac{1}{m}\sum_{i = 1}^m h_{D_i} \to \bar{h} \qquad as\  m \to \infty$$
Ensemble of Classifiers: Average of multiple classifiers 
If $\hat{h}\rightarrow \bar{h}$ then $\mathbb{E}[(\hat{h}(x)-\bar{h}(x))^2]\rightarrow 0$ but we only have $D$

## Bagging

Simulate drawing from P by drawing uniformly with replacement from the set $D$
Let $Q(X,Y|D)$ be a probability distribution that picks a training sample $(\vec{x_i}, yi)$ from $D$ uniformly at random

### Analysis 
Show new samples are drawn from the original distribution $P$ $$\begin{equation*}
\begin{aligned}
    Q(X=x_i)&= \underbrace{{\sum_{k = 1}^{n}}{n\choose k}p_i^k(1-p_i)^{n-k}}_{\substack{\text{Probability that are}\\\text{k copies of $x_i$ in D}}} \underbrace{\frac{k}{n}}_\mathrm{\substack{\text{Probability}\\\text{pick one of}\\\text{these copies}}}\\
    &=\frac{1}{n}\underbrace{{\sum_{k = 1}^{n}}{n\choose k}p_i^k(1-p_i)^{n-k}k}_{\substack{\text{Expected value of}\\\text{Binomial Distribution}\\\text{with parameter $p_i$}\\\mathbb{E}[\mathbb{B}(p_i,n)]=np_i}}\\
    &=\frac{1}{n}np_i\\
    &=p_i\leftarrow\text{Each data set $D'_l$ is drawn from P, but not independently.}
    \end{aligned}
\end{equation*}$$
### Summary
1. Sample $m$ data sets $D_1,\dots,D_m$ from $D$ with replacement
2. For each $D_j$ train a classifier $h_j()$
3. The final classifier is $h(\mathbf{x})=\frac{1}{m}\sum_{j=1}^m h_j(\mathbf{x})$

## Advantage of Bagging
- Easy to implement
- Reduces variance
- The prediction is an average of many classifiers so we obtain a mean score and variance, the latter can be interpreted as the uncertainty of the prediction
- Provides an unbiased estimate of the test error
	- Each training point was not picked and all the data sets $D_k$
	- If we average the classifiers $h_k$of all data sets we obtain a classifier that was not trained on $(\vec{x_i},y_i)$ and is the same as a test sample
	- For each training point $(\mathbf{x}_i,y_i)\in D$ let $S_i=\{k| (\mathbf{x}_i,y_i)\notin D_k\}$ be the set of all the training sets $D_k$ that does not have $(\vec{x_k},y_k)$
	- The averaged classifier over all these data sets: $\tilde h_i(\mathbf{x})=\frac{1}{|S_i|}\sum_{k\in S_i}h_k(\mathbf{x})$
	- The out of bag error is the average loss these classifiers yield: $\epsilon_\mathrm{OOB}=\frac{1}{n}\sum_{(\mathbf{x}_i, y_i) \in D}l(\tilde h_i(\mathbf{x_i}),y_i).$
	- This is an estimate of the test error because for each training point we used the subset of classifiers that never saw that training point during testing

## Random Forest

Bagged Decision Trees 

1. Sample m data sets $D_1,\dots,D_m$ with replacement
2. For each $D_j$ train a full decision tree $h_j()$ but before each split randomly subsample $k\leq d$ features without replacemenet and consider onyl these for your split
3. The final classifier is $h(\mathbf{x})=\frac{1}{m}\sum_{j=1}^m h_j(\mathbf{x})$

- Random Forest has only two hyperparameters $m$ and $k$ and its insensitive to both of these
- Does not need a lot of preprocessinig, so advantage if we have heterogenous data 

Variants of Random Forest:
- Do not grow each tree to its full depth. Prune based on the leave out samples
	- Imrproves bias variance trade off
- Split each training set into two partitions and build the tree on $D_l^A$ and estimate the leaf labels on $D_l^B$
	- Stop splitting if a leaf has only a single point in $D_l^B$
	- Each tree and athe RF is consistent