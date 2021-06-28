---
alias: PCA
---
# Principal Component Analysis (PCA)

The goal of PCA is to find a good linear subspace of the feature space onto which to project the data with minimal squared projection error. The subspace will by $k$ unit vectors $u^{(1)}$, ..., $u^{(k)}$. Thus PCA is a [[dimensionality reduction]] algorithm.

## PCA algorithm

We use the [[notation for learning algorithms]]. 

Note: This algorithm is taken from the [[Coursera course on machine learning]] and requires a proof. Use the below details with caution.

0. Perform [[feature scaling and mean normalization|mean normalization]] (so that we only need to consider surfaces going through the origin) and [[feature scaling and mean normalization|feature scaling]].
1. Compute the [[covariance|covariance matrix]]
	$$
	\Sigma = \frac1m \sum_{i=1}^m x^{(i)}(x^{(i)})^T = \frac1m XX^T \in \mathbb{R}^{n \times n}.
	$$
1. Compute the eigenvectors of $\Sigma$. Since $\Sigma$ is positive definite, one can do that by computing the [[singular value decomposition]] of $\Sigma$: $$\Sigma = USV^T.$$ Label the columns of $U = (u^{(1)} \cdots u^{(n)})$ and take the submatrix $U_{red} = (u^{(1)} \cdots u^{(k)})$ consisting of the first $k$ columns.
2. The new features are given by $z^{(i)} = U_{red}x^{(i)} \in\mathbb{R}^k$.

We note that the in terms of the original feature space, the obtained projection of $x$ is $x_{approx} = U_{red} z \in \mathbb{R}^n$.

## Choosing the number of principal components

- The averaged squared projection error in $\frac1m \sum_{i=1}^m \lVert x^{(i)} - x^{(i)}_{approx}\rVert^2$.
- The total variance in the data is $\frac1m \sum_{i=1}^m \lVert x^{(i)} \rVert^2$.
- The *fraction of variance preserved by dimensionality reduction* is $$1 - \frac{\frac1m \sum_{i=1}^m \lVert x^{(i)} - x^{(i)}_{approx}\rVert^2}{\frac1m \sum_{i=1}^m \lVert x^{(i)} \rVert^2}.$$ Writing $S = \operatorname{diag}(S_{11},\,\dots,\,S_{nn})$, this is the same [proof?] as $$ \frac{\sum_{i =1}^k S_{ii}}{\sum_{i=1}^n S_{ii}}.$$

Thus one picks a percentage of variance one wants to have preserved (e.g. 99% or 95%) an then takes $k$ to be the smallest value so that this is true.

## Advice for applying PCA

- PCA can be used for supervised learning speedup: having $x^{(i)} \in \mathbb{R}^n$ with $n$ large can lead to slow learning. Thus one could first apply PCA to obtain $z^{(i)}$ of lower dimension, and then train on $(z^{(i)},\, y^{(i)})$. To apply the obtained model to a new example $x$, always the PCA reduction matrix obtained from the training data first.
- Sometimes PCA is used to prevent [[variance|overfitting]]. This is not a good idea, and one should use [[regularization]] instead.
- Always ask whether PCA is actually necessary and try without first.