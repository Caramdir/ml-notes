# Gradient checking

For debugging purposes one can check the gradient computation in the [[00 - optimization algorithms|optimization algorithm]] numerically. 

Thus one approximates $\frac{\partial J}{\partial \theta_i}$ by
$$
	\frac{J(\theta_1,\dots,\theta_i+\epsilon,\dots,\theta_n) - J(\theta_1,\dots,\theta_i-\epsilon,\dots,\theta_n)}{2\epsilon}.
$$
Putteing these into a vector $\nabla_{approx}J$, then
$$
	\frac{\lVert\nabla_{approx}J - \nabla J\rVert}{\lVert\nabla_{approx}\rVert + \lVert\nabla J\rVert}
$$
should be on the order of $\epsilon$.

Numeric gradient approximation is computationally expensive and hence should only be used as a debugging tool.

One should not forget the [[regularization]] term in $J$ when computing the gradient. Gradient checking does not work with [[Supervised learning/Neural Networks/regularization|dropout regularization]] and any other method that adds randomness.