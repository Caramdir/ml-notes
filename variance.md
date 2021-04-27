---
alias: overfitting, high variance
---
# Variance in supervised learning
A [[00 - supervised learning]] model suffers from *high variance* or *overfitting*, if it predicts the training set very well, but fails to generalize to new examples.

This is often the case when the parameter space is large compared to the number of training examples. For example, it is possible to fit a high degree polynomial exactly to the data points in the training example in a [[00 - regression problem]], but that polynomial will oscillate wildly between the data points.

When a model has high variance, then the cost function is low on the [[training set]], but high on the [[cross-validation set]] and [[test set]].

Strategies to reduce variance include
- adding more training examples
- reducing the number of parameters in the model, e.g. by reducing the number of features.
- [[regularization]]