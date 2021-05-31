---
alias: dropout regularization
---
# Regularization

To avoid [[variance|high variance]] problems, it may be necessary to regularize the [[00 - neural networks|neural network]].

## Frobenius regularization

Recall that the *Frobenius norm* of a matrix $A$ is $\lVert A \rVert_F = \sqrt{\sum_{i,j} A_{i,j}^2}$.

To regularize a neural network, one can add a term $\frac{\lambda}{2m} \sum_{\ell=1}^L \lVert W^{[\ell]}\rVert_F^2$ to the cost function, where $\lambda$ is a [[hyperparameter]]. The corresponding partial derivative adds $\frac{\lambda}{m} W^{[\ell]}$ to $\frac{\partial J}{\partial W^{[\ell]}}$.

This is also called *weight decay* regularization

## Dropout regularization

In dropout regularization in each training example computation random node activations get zeroed out. Thus, after computing $a^{[\ell]}$ for some training example, one applies the following pseudo-Numpy code:
$$
\begin{aligned}
	d^{[\ell]} & = \text{np.random.rand}(a^{[\ell]}\text{.shape}) < \text{keep\_prop} \\
	a^{[\ell]} & = a^{[\ell]} * d^{[\ell]} \\
	a^{[\ell]} & /= \text{keep\_prob}
\end{aligned}
$$
Thus `keep_prop` is the chosen probability that any given unit will be kept. The last step ensures that we keep the expected value of $a^{[\ell]}$, which is necessary to make predictions with the trained network. Of course during backpropagation, we also use the modified $a^{[\ell]}$.

When making predictions at test time, one does not use any dropout.

The value of `keep_prop` can be varied by layer and should generally be lower for layers with more units.

The idea of dropout regularization is that the network cannot rely on any one features, so the weights need to be spread out. 

Dropout regularization tends to be very useful in computer vision, where one typically has many features, but not enough data to avoid overfitting.

When doing dropout regularization the cost function $J$ is no longer well defined (since it depends on a random choice), so it cannot be used to double-check gradient descent.

## Early stopping

Sometimes early stopping of the training/optimization process is used as a way to regularize a network. However, [[Andrew Ng]] recommends against doing so as it is against [[orthogonalization]]: gradient descent would then be a tool both for minimizing $J$ and preventing overfitting.