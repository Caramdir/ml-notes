# Collaborative filtering

A [[00 - recommender system]], where the features of the items are not known in advance. Instead the features are learned from the ratings.


## Idea

Suppose we know the parameters $\theta^{(j)}$ for predicting the ratings user $j$ assigns to items (as in [[content based recommendations]]). Then we can learn feature vectors $x^{(i)}$ for the items by minimizing
$$
	\frac12 \sum_{j: r(i,j) = 1} \bigl( (\theta^{(j)})^Tx^{(i)} - y^{(i,j)}\bigr)^2  + \frac{\lambda}2 \sum_{k=1}^n (x_k^{(i)})^2,
$$
where the second sum is for [[regularization]].

Thus we could guess random $\theta$, then learn $x$, then learn $\theta$, then learn $x$, ..., until the process converges.

## The optimization problem

This can be package into a single cost function one needs to minimize:
$$
	J(x^{(1)},\, \dots,\, x^{(n_i)},\, \theta^{(1)},\,\dots,\,\theta^{(n_u)}) =
	\frac12 \sum_{r(i,j) = 1} \bigl( (\theta^{(j)})^Tx^{(i)} - y^{(i,j)}\bigr)^2  + \frac{\lambda}2 \sum_{i=1}^{n_i}\sum_{k=1}^n (x_k^{(i)})^2 + \frac{\lambda}2 \sum_{j=1}^{n_u}\sum_{k=1}^n (\theta_k^{(j)})^2.
$$
(Note that there are no $\theta_0$ and $x_0$.) Thus we have the following steps:
1. Initialize $x$, $\theta$ with small random values.
2. Minimize $J$ over $x$, $\theta$, e.g. with [[gradient descent]].
3. Predict with $\theta^tx$.

To vectorize this problem, set
$$
	\begin{aligned}
		Y & = \bigl(y^{(i,j)}\bigr)_{i,j} \\
		X &= \begin{pmatrix}
			| & | & & | \\
			x^{(1)} & x^{(2)} & \cdots & x^{(n_i)} \\
			| & | & & |
		\end{pmatrix} \\
		\Theta &= \begin{pmatrix}
			| & | & & | \\
			\theta^{(1)} & \theta^{(2)} & \cdots & \theta^{(n_u)} \\
			| & | & & |
		\end{pmatrix} \\
	\end{aligned}
$$
We than have to compute $X^T\Theta$.

Note that $X^T\Theta$ is usually low rank and the algorithm is hence sometimes called *low rank matrix factorization* [TODO: details?]

## Finding related items

After learning $x^{(i)}$ as above, we can find items $\ell$ related to a given item $i$ by taking those with $\lVert x^{(i)} - x^{(\ell)}\rVert$ small.

## Mean normalization
There might be users with no ratings. For those the above algorithm returns $\theta = 0$.

Let $\mu \in \mathbb{R}^{n_i}$ be the average rating of each item and replace $Y$ by $Y - \mu$, so that each item has an average rating of $0$.

Predict $(\theta^{(j)})^Tx^{(i)} + \mu_i$. So for users with no ratings we now predict $\mu_i$.