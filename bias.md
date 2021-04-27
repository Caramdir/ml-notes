---
alias: underfitting, high bias
---
# Bias is supervised learning
A supervised learning model is subject to *high bias* or *underfitting*, if it does not fit the [[training set]] well, i.e., if the cost function on the training set is high. In other words, it does not make good predictions when evaluated at training examples.

When a model has high bias, then the cost functions on both the training set and [[cross-validation set]] (or [[test set]]) are high.

Strategies to reduce bias include:
- Adding additional parameter to the model, e.g. by adding more features or using [[polynomial regression|polynomial features]].
- Decreasing the [[regularization|regularization parameter]].