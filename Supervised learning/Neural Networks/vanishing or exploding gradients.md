# Vanishing/exploding gradients

By the chain rule, gradients accumulate multiplicatively over layer, and this exponential growth or decay can be a problem with very deep neural networks.

As the multiplicative factors on the gradients essentially depend on the size of the weights, one might thus want smaller initialization values for larger layers.

Different initialization techniques are discussed in [Kumar, arXiv:1704.08863](https://arxiv.org/pdf/1704.08863.pdf)

## He initialization

In [He et al., arXiv:1502.01852](https://arxiv.org/pdf/1502.01852.pdf) it is suggested to initialize the weights of layers with [[ReLU]] [[nonlinearity|activiation function]] $\ell$ with a normal distribution with mean zero and variance $\sqrt{\frac{2}{n^{[\ell]}}}$.

## Xavier initialization

For [[tanh]] [[nonlinearity|activiation]], Kumar suggests to use *Xavier initialization,* i.e. a normal distribution with mean 0 and variance $\sqrt{\frac1{n^{[\ell]}}}$.