# Cross-entropy

Given two probability distributions $p$ and $q$ on a finite set $\mathcal X$, their *cross-entropy* is defined to be
$$
	H(p,q) = -\mathbb{E}_p[\log q] = -\sum_{x \in \mathcal X} p(x)\log q(x).
$$
That is, it is the expected number of bits (if the base of $\log$ is 2) needed to identify an object drawn from $\mathcal X$ using a coding scheme that is optimized for the distribution $q$, rather than the true distribution $p$.

We note that if $q = p$ one obtains the [entropy](https://en.wikipedia.org/wiki/Entropy_(information_theory)) of $p$.

## Relation to [[likelihood function|maximum likelihood estimation]]
Given samples of size $N$ from $\mathcal X$ let $p(x)$ be the frequency of the outcome $x$ as proportion of total outcomes. Then the [[likelihood function|likelihood]] of a probability distribution $q$ on $\mathcal{X}$ is
$$
	\prod_x q(x)^{Np(x)}.
$$
Taking $\log$ and dividing by $N$, one obtains
$$
	\sum p(x)\log q(x) = - H(p, q).
$$
Thus maximizing the likelihood is the same as minimizing the cross entropy $H(p, q)$.

