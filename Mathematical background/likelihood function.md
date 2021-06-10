---
alias: likelihood, maximum likelihood estimation, MLE
---
# Likelihood function

Given an observation $x$ if a discrete random variable $X$, the *likelihood* of a probability distribution $p$ given $x$ is
$$
	p(x) = \mathbb{P}(X = x).
$$
If $p = p_\theta$ depends on a parameter $\theta$, then the function
$$
	\mathcal{L}(\theta | x) = 
	p_\theta(x) =
	\mathbb{P}_\theta(X = x ),
$$
considered as a function in $\theta$, is the *likelihood function* given the outcome $x$ of the random variable $X$.

The *maximum likelihood estimation* (*MLE*) of $\theta$ is the value of $\theta$ that maximizes the likelihood function.
