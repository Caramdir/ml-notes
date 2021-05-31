---
alias: batch gradient descent
---
# Gradient descent

Given a function $J(\theta)$ with $\theta \in \mathbb{R}^n$, we want find a value for $\theta$ minimizing $J$.

Let 
$$
	\nabla J(\theta) = 
	\begin{pmatrix}
		\frac{\partial J}{\partial \theta_1} \\
		\vdots \\
		\frac{\partial J}{\partial \theta_n}
	\end{pmatrix}
$$
be the gradient of $J$. Fix a *learning rate* $\alpha >0$.

**Algorithm**:
- Initialize $\theta$ with some guess.
- Repeatedly update	$$\theta = \theta - \alpha \nabla J(\theta).$$	until convergence.

A larger learning rate $\alpha$ can mean faster convergence, but if $\alpha$ is too large, the process might diverge.

It can be useful to plot the value of $J(\theta)$ against the number of iterations of the descent step. If the plot diverges or oscillates, then $\alpha$ is too large. On the other hand, if convergence is too slow, then increasing $\alpha$ can be beneficial (though sometimes slow convergence also happens if $\alpha$ is too large).

One might try different learning rates to find an optimal one, e.g. increasing in powers of then, or by a factor of roughly $3$, e.g. $\alpha = \dots,\, 0.001,\, 0.003,\, 0.01,\, 0.03,\, 0.1,\, \dots$.

Instead of gradient descent it can be advantageous to use a more sophisticated algorithm (such as conjugate descent, BFGS or L-BFGS). In this case it is recommended to use library code.

As this algorithm uses the whole [[training set]] at once, is is also called *batch gradient descent.* Running gradient descent with only a portion of the [[training set]] at a time gives [[mini-batch gradient descent]].