---
alias: SVM
---
# Support vector machine

Starting with [[logistic regression]], one modifies the cost function: instead of
$$
	J(\theta) = -\frac1m \sum_{i=0}^m \bigl(y^{(i)}\log(g(\theta^Tx^{(i)})) + (1-y^{(i)})\log(1-g(\theta^Tx^{(i)}))\bigr) + \frac{\lambda}{2m} \sum_{j=1}^n \theta_j^2,
$$
with $g$ the [[logistic function]], one sets
$$
	J(\theta) = C\sum_{i=0}^m \bigl(y^{(i)}\operatorname{cost}_1(\theta^Tx^{(i)}) + (1-y)\operatorname{cost}_0(\theta^Tx^{(i)})\bigr) + \frac{1}{2} \sum_{j=1}^n \theta_j^2,
$$
where $C$ is a new parameter (corresponding to $\frac1\lambda$) and
$$
	\begin{aligned}
		\operatorname{cost}_0(z) &= \max(0, z+1), \\
		\operatorname{cost}_1(z) &= \max(0, -z+1).
	\end{aligned}
$$
One predicts $y =1$ if $\theta^Tx \ge 0$.

## Large margin intuition
The parts of the cost function have a similar graph as the corresponding parts of the cost function for [[logistic regression]] [todo: add plots]. The idea of the shift by $1$ is to force the decision boundary to have a large margin to data points.

To see this let $C \to \infty$. Then the first part of the cost function forces
$$
	\begin{aligned}
	\theta^Tx^{(i)} & \ge 1	&\text{if } y^{(i)} = 1,\\
	\theta^Tx^{(i)} & \le -1 &\text{if } y^{(i)} = 0.
	\end{aligned}
$$
Assume for simplicity that $\theta_0 = 0$. Thus the goal becomes to minimize $\lVert\theta\rVert$ under these constraints.

Note that $\theta^Tx^{(i)} = p^{(i)}\lVert \theta\rVert$, where $p^{(i)}$ is the signed length of the projection of $x^{(i)}$ onto $\theta$. If the decision boundary avoids data points, then its normal vector $\theta$ points directly to the data points, making the $p^{(i)}$ as large as possible. Thus in this case $\lVert\theta\rVert$ can be minimal while still satisfying the constraints.

## Kernels

In the setting of SVMs, a *kernel* or *similarity* is a symmetric function $k(x, x')$  on the feature space such that $k(x,x) = 1$ and $k(x, x') \to 0$ and the distance between $x$ and $x'$ goes to $\infty$. One example is the *Gaussian kernel*
$$
	k(x,x') = \frac{\lVert X - x'\rVert^2}{2\sigma^2}
$$
for some $\sigma \in \mathbb{R}$.

One can use kernels to add new features: Fixing a *landmark* $\ell$ in the feature space, one takes $k(x, \ell)$ as a new feature.

In SVM one takes landmarks at each training example, so that each example $x$ gets replaced by a new vector $f \in \mathbb{R}^{m+1}$ with $f_0 = 1$ and $f_j = k(x, x^{(j)})$. Thus, not counting the intercept, there are as many features as training examples.

SVM then minimizes the cost function
$$
	C\sum_{i=0}^m \bigl(y^{(i)}\operatorname{cost}_1(\theta^Tf^{(i)}) + (1-y)\operatorname{cost}_0(\theta^Tf^{(i)})\bigr) + \frac{1}{2} \sum_{j=1}^m \theta_j^2,
$$
and predicts $1$ if and only if $\theta^Tf \ge 0$.

## SVMs in practice

- The [[hyperparameter|hyperparameters]] have the following effects:
	- large $C$: lower bias, higher variance
	- small $C$: higher bias, lower variance
	- large $\sigma^2$: features $f_i$ vary more smoothly: higher bias, lower variance
	- small $\sigma^2$: features $f_i$ vary less smoothly: lower bias, higher variance
- The regularization term may be replaces by $\theta^T M \theta$ for some matrix $M$ depending on the kernel to improve optimization behavior.
- Use off-the-shelf packages rather than reimplementing SVM.
- Options for kernels include:
	- no kernel (also called *linear kernel*), e.g. when $n$ is large and $m$ small
	- Gaussian kernel, e.g. when $n$ is small or $m$ is large. Note that one should do feature scaling first.
	- Other kernels, satsifying *Mercer's Theorem*, e.g. polynomial kernels, string kernel (for working with text strings), $\chi^2$-kernel, histogram intersection kernel
- For multi-class classification either use built-in support in the implementation package or use [[one-vs-all algorithm|one-vs-all]].
- logistic regression vs SVM:
	- $n$ large vs. $m$: use logistic regression or SVM without kernel
	- $n$ small, $m$ intermediate: Gaussian kernel
	- $n$ small, $m$ large: Gaussian kernel might be too slow. If so, create/add more features and use logistic regression or SVM without kernel
	- note: [[neural network|neural networks]] likely to work well for most of these settings, but may be slower to train.
- Remark: SVMs have convex optimization problems.