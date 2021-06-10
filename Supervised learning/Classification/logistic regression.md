# Logistic regression

An algorithm for binary classification with $y \in \{0,\,1\}$. 

We use the [[notation for learning algorithms]].

**Idea**: The hypothesis should give a probability for $y$ to be $1$. 

Logistic regression uses a [[linear regression]] followed by a [[logistic function]] $g$. As in linear regression, we add a term $x_0 = 0$ to the feature vector. Thus the hypothesis is $$h_\theta(x) = g(\theta^Tx)$$ with $\theta \in \mathbb{R}^{n+1}$.

As noted above, this is interpreted as $$h_\theta(x) = \mathbb{P}(y =1\, |\, x;\, \theta),$$
and we predict $y = 1$ if $h_\theta(x) \ge 0.5$. Equivalently, this is the case if $\theta^Tx \ge 0$.

The hyperplane $\theta^Tx = 0$ is called the *decision boundary*. Similar to [[polynomial regression]], we can add powers and other functions in the features to obtain more complex decision boundaries.

Using squared-error as cost function gives a non-convex optimization problem. One uses the following cost function instead:
$$
	J(\theta) =
	\frac1m \sum_{i=1}^m \operatorname{Cost}\bigl(h_\theta(x^{(i)}),\, y^{(i)}\bigr), 
$$
with
$$
	\operatorname{Cost}(\hat y, y) = -\bigl(y\log(\hat y) + (1-y)\log(1-\hat y)\bigr).
$$
As $y$ is always either $0$ or $1$, only one of the summands in $\operatorname{Cost}$ is nonzero for any given training example. The logarithm penalizes big errors in likelyhood much stronger than small ones.

The cost function is exactly the [[cross-entropy]] between the observed distribution and the one represented by the model (with parameter $\theta$). Thus minimizing the cost function is [[likelihood function|maximum likelihood estimation]] for $\theta$.

The partial derivatives of $J$ are
$$
	\frac{\partial}{\partial \theta_j} J(\theta) =
	\frac1m\sum_{i=1}^m\bigl(h_\theta(x^{(i)}) - y^{(i)}\bigl)x_j^{(i)}.
$$
Thus, in vectotized form the gradient of $J$ is
$$
	\nabla J(\theta) = \frac1m X\bigl(g(\theta^TX) - Y\bigr)^T.
$$

Since logistic regression is based on [[linear regression]], [[feature scaling and mean normalization|feature scaling]] is often necessary.

Logistic regression can be turned into a multiclass classifier via the [[one-vs-all algorithm]].

## Regularized logistic regression

The cost function for [[regularization|regularized]] logistic regression with regularization parameter $\lambda$ is
$$
	J(\theta) =
	\frac{1}{2m} \biggl(
	\sum_{i=1}^m \operatorname{Cost}\bigl(h_\theta(x^{(i)}),\, y^{(i)}\bigr) +
	\lambda \sum_{j=1}^n \theta_j^2\biggr).
$$
Note that one does not penalize the intercept term $\theta_0$. Writing $\hat\theta$ for the vector $\theta$ with $\hat\theta_0=0$, the gradient is
$$
\nabla J(\theta) = \frac1m \Bigl( X\bigl(g(\theta^TX) - Y\bigr)^T +\lambda\hat\theta\Bigr).
$$
One notes that in gradient descent this corresponds to gradient descent with the original cost function, where in each step the parameters $\theta_i$ are first multiplied by $1-\alpha\frac\lambda m < 1$.