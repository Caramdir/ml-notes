---
alias: likelihood, maximum likelihood estimation, MLE, negative log loss
---
# Likelihood function

Given an observation $x$ if a discrete random variable $X$, the *likelihood* of a probability distribution $p$ given $x$ is
$$
	p(x) = \mathbb{P}(X = x).
$$
If $p = p_\theta$ depends on a parameter $\theta$, then the function
$$
	\mathcal{L}(\theta | x) = 
	p(x|\theta) =
	\mathbb{P}(X = x|\theta),
$$
considered as a function in $\theta$, is the *likelihood function* given the outcome $x$ of the random variable $X$.

The *maximum likelihood estimation* (*MLE*) of $\theta$ is the value of $\theta$ that maximizes the likelihood function. This is the [[maximum a posterior estimation]] with uniform prior.

Usually, the observation consists of $m$ identically and independently distributed samples $x_i$. In this case, the loss function decomposes and the MLE is
$$
	\operatorname*{argmax}_{\theta}\prod_{i} p(x_i|\theta).
$$
It is often convenient to take a logarithm and minimize the *negative log loss* instead:
$$
	\operatorname*{argmin}_\theta \Bigl(-\sum_i p(x_i|\theta)\Bigr).