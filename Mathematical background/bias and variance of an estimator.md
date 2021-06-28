---
alias: bias of an estimator, unbiased, unbiased estimator, variance of an estimator
---

# Bias and variance of an estimator

Let $\mathcal{D}$ be data drawn from an unknown distribution $p^*$. An estimator $\hat\theta(\cdot)$ is a rule associating to $\mathcal D$ an estimation for a parameter $\theta$.

## Bias

The *bias* of an estimator is 
$$
	\operatorname{bias}(\hat\theta(\cdot)) = \mathbb E[\hat\theta(\mathcal D)] - \theta^*,
$$
where $\theta^*$ is the true value of $\theta$ and the expected value is taken over $\mathcal D \sim p^*$.

An estimator is *unbiased* if its bias is $0$.

For example, the [[likelihood function|MLE]] $\frac1N 
\sum x_i$ for a Gaussian mean is unbiased. However, the MLE  $\frac1N \sum (x_i - \bar x)^2$ for Gaussian variance is biased. This is due to the fact that the same data points are used to compute the mean. The unbiased estimator for Gaussian variance is $\frac1{N-1} \sum (x_i - \bar x)^2$. However is the true mean $\mu$ is known, then the MLE $\frac1N \sum (x_i - \mu)^2$ is unbiased.

## Variance

The *variance* of the estimator $\hat \theta(\cdot)$ is defined to be
$$
	\mathbb{V}[\hat \theta(\cdot)] = \mathbb E[\hat\theta(\mathcal D)^2] - \mathbb E[\hat \theta(\mathcal D)]^2,
$$
where the expected value is taken over the true distribution $\mathcal D \sim p^*$

## The bias-variance tradeoff

A direct computation shows that the mean squared error of the estimate $\hat\theta(\mathcal D)$ is 
$$
	\mathbb E[(\hat\theta(D) - \theta^*)^2] =
	\mathbb V[\hat \theta] + \operatorname{bias}(\hat\theta)^2,
$$
where again the expected value is taken over $\mathcal D \sim p^*$. Thus in order to obtain a minimal mean squared error, it may be optimal to use a biased estimator as long as it has less variance.