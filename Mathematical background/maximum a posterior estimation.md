---
alias: MAP, posterior predictive distribution
---
# Maximum a posterior estimation

Given an observation $x$ from a random variable, the *maximum a posterior estimation* (or *MAP*) is a Bayesian way to estimate a parameter $\theta$ for the distribution of $\theta$.

One starts with *prior distribution* $p(\theta)$ for $\theta$ and uses [[Bayes' theorem|Bayes' rule]] to update it based on the observation:
$$
	p(\theta|x) = \frac{p(\theta) p(x | \theta)}{p(x)}.
$$
Here $p(x|\theta)$ is the [[likelihood function]] and $p(x)$ is the *marginal likelihood*
$$
	p(x) = \int_{\theta'} p(\theta')p(x|\theta') d\theta'.
$$
The MAP estimation for $\theta$ is the mode
$$
	\operatorname*{argmax}_\theta p(\theta|x).
$$
We note that the denominator $p(x)$ does not depend on $\theta$ and can hence be ignored in the computation.

If the prior $p(\theta)$ is uniform, then the term $p(\theta)$ can also be ignored and the MAP estimation reduced to the [[likelihood function|maximum likelihood estimation]].

One can also use $p(\theta|x)$ to obtain the *posterior predictive distribution* for a new observation $x'$:
$$
	p(x' | x) = \int_\theta p(x' | \theta)p(\theta|x)d\theta.
$$