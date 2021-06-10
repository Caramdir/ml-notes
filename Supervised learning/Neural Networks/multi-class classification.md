---
alias: softmax
---
# Multi-class classification with softmax regression

Let $C$ be the number of classes. Then the number of nodes in the output layer should be $n^{[L]} = C$ and the individual nodes should output the probability that $x$ is in the corresponding class. In particular, the outputs should sum up to $1$.

Given $z^{[L]}$ use the following [[nonlinearity|activiation function]]: First compute
$$
	t = e^{z^{[L]}} \in \mathbb{R}^{n_L \times 1}
$$
and then
$$
	a^{[L]} = \frac{t}{\sum_{j=1}^{n_L} t_j}
$$
This is the *softmax activiation function* (as compared to *hardmax*, which outputs $1$ for the biggest component and $0$ elsewhere). When $C=1$ this reduces to a [[logistic function]].

The corresponding loss function is [[cross-entropy]],
$$
	\mathcal{L}(\hat y, y) = -\sum_{j=1}^C y_j \log \hat y_j.
$$
Note that $y_j \in \{0,1\}$ with exactly one $y_j = 1$. The cost function is as usual
$$
	J = \frac1m \sum_{i=1}^m \mathcal{L}(\hat y^{(i)}, y^{(i)}).
$$
For back-propagation we have
$$
	dz^{[\ell]} = \frac{\partial J}{\partial z^{[\ell]}} = \hat y - y.
$$
[TODO: check.]