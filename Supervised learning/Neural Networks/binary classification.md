# Binary classification with neural networks

For binary classification, we have a single node in the output layer ($n^{[L]}=1$) with a [[logistic function]] as [[nonlinearity]].

The loss functions is (as for [[logistic regression]])
$$
	\mathcal L(\hat y, y) = -\bigl(y\log \hat y + (1-y)\log(1-\hat y)\bigr).
$$
Thus,
$$
	\frac{\partial J}{\partial A^{[L]}} = \frac1m \sum_{i=1}^m\Bigl(-\frac{y^{(i)}}{a^{[L](i)}} + \frac{1-y^{(i)}}{1-a^{[\ell](i)}}\Bigr).
$$