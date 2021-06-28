---
alias: covariance, covariance matrix, cross-covariance
---

# Covariance

The *covariance* of two [[random variables]] $X$ and $Y$ is
$$
	\operatorname{Cov}[X, Y] = \mathbb E\bigl[(X - \mathbb{E}[X])(Y - \mathbb E[Y])\bigr] = \mathbb E[XY] - \mathbb E[X]\mathbb E[Y].
$$
The covariance measures the degree to which $X$ and $Y$ are linearly related. Note that the magnitude of the covariance depends on the magnitudes of $X$ and $Y$. A normalized version is [[correlation]].
![[170px-Covariance_trends.svg.png|Source: Wikipedia]]

If $X = Y$, then $\operatorname{Cov}[X, X] = \mathbb \sigma_X^2$ is the [[Mathematical background/variance|variance]] of $X$.

The *covariance matrix* of a random vector $\mathsf X$ is
$$
	\operatorname{Cov}[\mathsf X] = \Sigma_{\mathsf X} =
	\mathbb E\bigl[(\mathsf X - \mathbb E[\mathsf X])(\mathsf X - \mathbb E[X])^T\bigr] =
	(\operatorname{Cov}[\mathsf X_i, \mathsf X_j])_{i,j}.
$$
Further, the *cross-covariance* between two random vectors $\mathsf X$ and $\mathsf Y$ is the matrix
$$
	\operatorname{Cov}[\mathsf X,\mathsf Y] =
	\mathbb E\bigl[(\mathsf X - \mathbb E[\mathsf X])(\mathsf Y - \mathbb E[Y])^T\bigr] =
	(\operatorname{Cov}[\mathsf X_i, \mathsf Y_j])_{i,j}.
$$