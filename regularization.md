---
alias: regularization parameter
---
# Regularization

*Regularization* is the idea of keeping the magnitude of parameters small in order to combat [[variance|high variance]]. This is usually done by adding an extra term to the cost function involving the parameters. This term might depend on a parameter, called the *regularization parameter*.

Regularization works particulalrly well when there are lots of slighly useful features.

To [[model selection|select]] the regularization parameter, one can plot the (unregularized) cost function of both the [[training set]] and [[cross-validation set]] versus the regularization parameter and select the one with best performance on the [[cross-validation set]].

Typically a small parameter will lead to [[variance|high variance]], while a large parameter will lead to [[bias|high bias]].