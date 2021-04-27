# Anomaly detection

Given a dataset $\{x^{(i)}\}$ of "normal" examples, decide whether a new example $x_{test}$ is anomalous, i.e. compute a probability for it to be anomalous.

We use the [[notation for learning algorithms]].

In anomaly detection on usually has few or none positive examples in the training data, but a large number of negative examples. Typically there are many different types of positive examples and future types of anomalies might be different from ones already encountered.

On the other hand, if one has both a large number of positive and negative examples in the training data, a [[00 - supervised learning]] algorithm might be more applicable to the problem.

Typical applications of anomaly detection include fraud detection and manufacturing (unless there are lots of examples available).

## Anomaly detection using Gaussian distribution

Write $x \sim \mathcal{N}(\mu, \sigma^2)$ for $x$ distributed by a Gaussian (or normal) distribution with mean $\mu$ and variance $\sigma^2$. Thus $x$ has density function
$$
	f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}.
$$
Given data $x^{(1)}$, ..., $x^{(m)} \in \mathbb{R}$ which is assumed to come from a Gaussian distribution, one estimates
$$
	\begin{aligned}
		\mu &= \frac1m\sum_{i=1}^m x^{(i)}, \\
		\sigma^2 &= \frac1m\sum_{i=1}^m (x^{(i)}-\mu)^2.
	\end{aligned}
$$
[The divisor in the variance formula might be $m-1$. Why? In any case this doesn't make much difference large data sets.]

Assume we are given data $x^{(1)}$, ..., $x^{(m)} \in \mathbb{R}^n$ such that each feature $x_i$ is independently normal distributed, say $x_i \sim \mathcal N(\mu_i, \sigma_i^2)$, estimated as above.

Take
$$
	p(x) = \prod_{j=1}^n p(x_j;\, \mu_j,\, \sigma_j^2).
$$
Then $x$ is anomalous if $p(x) < \epsilon$, for some fixed parameter $\epsilon$.

## Anomaly detection using multivariate Gaussian distribution

Dropping the independence assumption, one can model the probability with a multivariate Gaussian distribution with density
$$
	p(x) = \frac1{(2\pi)^{n/2}|\Sigma|^{\frac12}} \exp\bigl(-\frac12 (x-\mu)^T\sigma^{-1}(x-\mu)\bigr),
$$
where $\mu \in \mathbb{R}^n$ and $\Sigma \in \mathbb{R}^{n \times n}$. The entries of the *covariance matrix* $\Sigma$ determine how much any two given features (anti)correlate.

The parameters are estimated as
$$
	\begin{aligned}
		\mu &= \frac1m\sum_{i=1}^m x^{(i)}, \\
		\Sigma &= \frac1m\sum_{i=1}^m (x^{(i)}-\mu)(x^{(i)}-\mu)^T.
	\end{aligned}
$$

**Notes:**
- This is computationally more expensive that the univarate Gaussians above.
- If $m < n$ (or there are linearly dependent features), the matrix $\Sigma$ might be non-invertible.
- There are $O(n^2)$ parameters, so in practice one needs sufficent data to train $\Sigma$ well.

## Practical considerations

- The training set is unlabeled data, consisting of mostly non-anomalous examples
- The [[cross-validation set|cv set]] and [[test set]] should have some anomalous examples. So split the known anomalous examples between these sets.
- Possible metrics include
	- [[precision and recall|true positive]], [[precision and recall|false positive]], [[precision and recall|true negative]], [[precision and recall|false negative]]
	- [[precision and recall]]
	- [[F1 score|$F_1$ score]]
- One can use the [[cross-validation set|cv set]] to chose the parameter $\epsilon$.
- Plot each feature to make sure that it is vaguely Gaussian.
- If not, transform data to make it more Gaussian (e.g. by taking $\log$ or roots).
- Use [[error analysis]] to come up with new features.
- Choose features that might take on unusually large or small values.