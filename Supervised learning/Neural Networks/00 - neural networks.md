---
alias: neural network, neural networks
---
# Neural networks

Neural networks consist of a number of *layers*, each in turn consisting of several *nodes* or *units*. The output of the nodes of one layer serves as the input of nodes to the next layer.

[TODO: Add picture.]

The motivation for neural networks is that each layer builds upon the previous layer. In this way one can build complex functions out of simple ones.

We let $L$ be the number of layers with computation nodes. In addition there is a 0th layer, called the *input layer,* containing the data. The last layer (layer $L$) is called the *output layer.* All other layers are called *hidden layers.*

We write $n^{[\ell]}$ for the number of nodes in the $\ell$th layer, and $a^{[\ell]} \in \mathbb{R}^{n^{[\ell]}}$ for the output of the nodes in the $\ell$th layer when then network is applied to some data vector $a^{[0]} = x$. 
We call $a^{[\ell]}$ the *activation* of the layer. As usual, when vectorizing we set $A^{[0]} = X$ and let $A^{[\ell]} \in \mathbb{R}^{n^{[\ell]}\times m}$ be the matrix of activations of the $\ell$th layer at the $x^{(i)}$. Computation of $A^{[L]}$ from $X$ is called *forward propagation.*

While in principle the nodes could compute arbitrary functions, the term *neural network* usually refers to the case where each node is an affine function followed by a *[[nonlinearity]]* or *activation function*. That is, the $i$th node in the $\ell$th layer computes
$$
	a_i^{[\ell]} = g^{[\ell]}\bigl(w_i^{[\ell]T} a^{[\ell-1]} + b_i^{[\ell]}\bigr),
$$
where $w_i^{[\ell]} \in \mathbb{R}^{n^{[\ell-1]}}$, $b_i^{[\ell]} \in \mathbb{R}$ and $g^{[\ell]}$ is a nonlinearity. Setting
$$
	W^{[\ell]} = 
	\begin{pmatrix}
		w_1^{[\ell]T} \\
		\vdots \\
		w_{n^{[\ell]}}^{[\ell]T} \\
	\end{pmatrix} \in \mathbb{R}^{n^{[\ell]} \times n^{[\ell-1]}}
	\qquad\text{and}\qquad
	b^{[\ell]} = 
	\begin{pmatrix}
		b_1^{[\ell]} \\
		\vdots \\
		b_{n^{[\ell]}}^{[\ell]} \\
	\end{pmatrix} \in \mathbb{R}^{n^{[\ell]}},
$$
we have
$$
	A^{[\ell]} = g^{[\ell]}\bigl(W^{[\ell]}A^{[\ell-1]} + b^{[\ell]}\bigr).
$$
The result of the affine part of the computation is denoted $Z^{[\ell]} = W^{[\ell]}A^{[\ell-1]} + b^{[\ell]}$.

The choice of $L$, $n^{[\ell]}$ and $g^{[\ell]}$ is the *architecture* of the network, while $W^{[\ell]}$ and $b^{[\ell]}$ are considered parameters.

## Training of a neural network

Let $\mathcal L$ be the loss function for a single example and $J = \frac1m \sum_{i=1}^m \mathcal L(\hat y^{(i)},\, y^{(i)})$ the corresponding cost function over the training set. As usual, we view $J$ as a function in the parameters
 $W^{[\ell]}$ and $b^{[\ell]}$. For training we need to compute all the partial derivatives of $J$.

For a single training example, we have
$$
	\frac{\partial \mathcal L}{\partial W^{[\ell]}_{i,j}} =
	\sum_{k=1}^{n^{[\ell]}}	\frac{\partial z_k^{[\ell]}}{\partial W^{[\ell]}_{i,j}} \frac{\partial \mathcal L}{\partial z_k^{[\ell]}} =
	\frac{\partial z_i^{[\ell]}}{\partial W^{[\ell]}_{i,j}} \frac{\partial \mathcal L}{\partial z_i^{[\ell]}} =
	a_j^{[\ell-1]}\frac{\partial \mathcal L}{\partial z_i^{[\ell]}},
$$
where the second equality follows from $\frac{\partial z_k^{[\ell]}}{\partial W^{[\ell]}_{i,j}} = 0$ for $i \ne k$. It follows that
$$
	\frac{\partial \mathcal L}{\partial W^{[\ell]}} = 
	\frac{\partial \mathcal L}{\partial z^{[\ell]}} \cdot a^{[\ell-1]T}
$$
and hence
$$
	\frac{\partial J}{\partial W^{[\ell]}} =
	\frac1m\frac{\partial \mathcal L}{\partial Z^{[\ell]}} \cdot A^{[\ell-1]T}.
$$
Similarly,
$$
	\frac{\partial \mathcal L}{\partial b^{[\ell]}} =
	\frac{\partial \mathcal L}{\partial z^{[\ell]}}
$$
and hence $\frac{\partial J}{\partial b^{[\ell]}}$ is $\frac1m$ times the sum over the rows of $\frac{\partial J}{\partial Z^{[\ell]}}$.

Further, since $A^{[\ell]} = g^{[\ell]}(Z^{[\ell]})$ with coefficient-wise application of $g^{[\ell]}$,  the chain rule implies that $\frac{\partial J}{\partial Z^{[\ell]}}$ is the coefficient-wise product of $\frac{\partial J}{\partial A^{[\ell]}}$ and $g^{[\ell]\prime}\bigl(\frac{\partial J}{\partial Z^{[\ell]}}\bigr)$. Finally,
$$
	\frac{\partial \mathcal L}{\partial a^{[\ell-1]}_i} =
	\sum_{j=1}^{n^{[\ell]}} \frac{\partial z_j^{[\ell]}}{\partial a_i^{[\ell-1]}}\frac{\partial \mathcal L}{\partial z_j^{[\ell]}} =
	\sum_{j=1}^{n^{[\ell]}} W_{j,i}^{[\ell]}\frac{\partial \mathcal L}{\partial z_j^{[\ell]}}
$$
and hence
$$
	\frac{\partial J}{\partial A^{[\ell-1]}} = W^{[\ell]T} \cdot \frac{\partial J}{\partial Z^{[\ell]}}.
$$

Summarizing this as Python/Numpy pseudo-code, the partial derivatives can be recursively computed by
$$
\begin{aligned}
	\frac{\partial J}{\partial Z^{[\ell]}} & = \frac{\partial J}{\partial A^{[\ell]}} * g^{[\ell]\prime}\bigl(\frac{\partial J}{\partial Z^{[\ell]}}\bigr) \\
	\frac{\partial J}{\partial W^{[\ell]}} & =
	\frac1m * \frac{\partial J}{\partial Z^{[\ell]}} \mathbin{@} A^{[\ell-1]T} \\
	\frac{\partial J}{\partial b^{[\ell]}} &= \frac1m * \mathrm{np.sum}\bigl(\frac{\partial J}{\partial Z^{[\ell]}},\, \mathrm{axis}=1\bigr) \\
	\frac{\partial J}{\partial A^{[\ell-1]}} &= W^{[\ell]T} \mathbin@ \frac{\partial J}{\partial Z^{[\ell]}}
\end{aligned}
$$
This process is called *backpropagation.* According to [[Andrew Ng]], the partial derivatives are usually denoted with variable names `dZ[l]`, `dW[l]`, `db[l]` and `dA[l-1]` respectively.

We note that only the computation step for $\frac{\partial J}{\partial A^{[L]}}$ directly depends on the chosen cost function. We further note that for efficient computation it is necessary to cache $A^{[\ell]}$ and (depending on the [[nonlinearity]]) $Z^{[\ell]}$ during forward-propagation for use in back-propagation.

After back-propagation, the parameters are then updated with the chosen [[00 - optimization algorithms|optimization algorithm]]. Before the first training step, the weights $W^{[\ell]}$ have to be initialized with (small) random numbers, as otherwise all nodes in each layer will always have the same weights after each training step. This is called *symmetry breaking*. See [[vanishing or exploding gradients]] for different initialization techniques used in deep networks.

## Specific applications

- [[Supervised learning/Neural Networks/binary classification|binary classification]]
- [[Supervised learning/Neural Networks/multi-class classification|multi-class classification]]
- [[Supervised learning/Neural Networks/multi-task classification|multi-task classification]]

## Further considerations

- To avoid [[variance]] problems, it may be necessary to add [[Supervised learning/Neural Networks/regularization|regularization]].
- One should use [[feature scaling and mean normalization]] to speed up gradient descent.
- [[vanishing or exploding gradients]]
- [[batch normalization|Batch normalization]] may improve learning performance.

## Advanced neural networks
- [[convolutional neural network]]
