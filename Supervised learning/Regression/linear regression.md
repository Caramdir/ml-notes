---
alias: regularized linear regression
---
# Linear regression

We use the standard [[notation for learning algorithms]].

The hypothesis for linear regression is an affine function in the input variable, that is,
$$
	h_{w,b}(x) = w^Tx + b
$$
with $w \in \mathbb{R}^n$ and $b \in \mathbb{R}$. The value $b$ is called the *interceptor term*. Often (e.g. in the [[Coursera course on machine learning]]), one packages this slightly differently adding a $0$-th term $x_0 = 0$ to the input and taking a parameter vector $\theta \in \mathbb{R}^{n+1}$ so that
$$
	h_{\theta}(x) = \theta^Tx.
$$
We will also use this convention. Correspondingly, the matrix $X \in \mathbb{R}^{(n+1) \times m}$ is all $1$ in the first (or $0$-th) row.

If $n=1$, one speaks of *univariate linear regression*, or linear regression with one variable.

The most common cost function for linear regression is squared error:
$$
	J(\theta) =
	\frac{1}{2m} \sum_{i=1}^m \bigl(h_{\theta}(x^{(i)}) - y^{(i)}\bigr)^2 =
	\frac{1}{2m} (\theta^T X - Y)(\theta^T X - Y)^T
$$
The aim is to find a parameter $\theta$ which minimizes $J$. This can for example be obtained with [[gradient descent]]. (Note that the factor of $\frac12$ in $J$ is simply there to make the derivatives slighlty nicer. The factor $\frac1m$ -- i.e. taking the mean -- is of course not necessary for optimization, but helps in interpreting the value of $J$ independent of $m$.) The functtion $J$ is convex (proof?), hence it has unique minimum.

The partial derivatives of $J$ are
$$
	\frac{\partial}{\partial \theta_j} J(\theta) =
	\frac{1}{m} \sum_{i=1}^m (h_\theta(x^{(i)}) - y^{(i)})x^{(i)}_j,
$$
where we recall that $x^{(i)}_0 = 0$. Thus
$$
	\nabla J(\theta) = \frac1m X(\theta^TX - Y)^T.
$$

When using gradient descent (or a similar algorithm) for linear regression, it is often helpful to do [[feature scaling and mean normalization]].

Linear regression can easily be generalized to [[polynomial regression]], and with the same idea one can also express other functions in the features (e.g., roots or logarithms).

## Normal equation

Since $\nabla J(\theta) = 0$ is a linear system of equations in the parameters $\theta_i$, it is possible to solve directly for $\theta$:
$$
	\theta = (XX^T)^{-1}XY^T.
$$
If $m > n$ and the features are linearly independent, then $XX^T$ is always invertible [proof?]. Otherwise, one can use the [[singular value decomposition|pseudo-inverse]].

[[Feature scaling and mean normalization]] is not necessary when using the normal equation formula for computing linear regression.

**Note:** since matrix inversion is $(O(n^3))$ (or thereabouts?), inverting the $(n+1)\times (n+1)$-matrix $XX^T$ can be slow for large $n$. In this case [[gradient descent]] might be faster.

## Regularized linear regression

The cost function for [[regularization|regularized]] linear regression with regularization parameter $\lambda$ is
$$
	J(\theta) =
	\frac{1}{2m} \biggl(\sum_{i=1}^m \bigl(h_{\theta}(x^{(i)}) - y^{(i)}\bigr)^2 + \lambda \sum_{j=1}^n \theta_j^2\biggr).
$$
Note that one does not penalize the intercept term $\theta_0$. Writing $\hat\theta$ for the vector $\theta$ with $\hat\theta_0=0$, the cost function vectorizes as
$$
	J(\theta) =
	\frac{1}{2m} \biggl((\theta^T X - Y)(\theta^T X - Y)^T + \lambda \hat\theta^T\hat\theta\biggr).
$$
The corresponding gradient is
$$
\nabla J(\theta) = \frac1m \bigl( X(\theta^TX - Y)^T +\lambda\hat\theta\bigr).
$$
One notes that in gradient descent this corresponds to gradient descent with the original cost function, where in each step the parameters $\theta_i$ are first multiplied by $1-\alpha\frac\lambda m < 1$.

The normal equation for regularized linear regression is
$$
	\theta = \left(XX^T + \lambda
	\begin{pmatrix}
		0 &   & & \\
		  & 1 & & \\
		  &   &\ddots & \\
		  &   &       & 1
	\end{pmatrix}
	\right)^{-1}XY^T.
$$