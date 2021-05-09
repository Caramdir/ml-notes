# Advice on machine learning system design

The following steps are recommended in the [[Coursera course on machine learning]]:

- Start with a simple algorithm and test it on the [[cross-validation set|cv set]].
- Plot [[learning curves]] to see what is most likely to improve performance.
- Use [[error analysis]] to get ideas on how to improve the model.
- Use a [[performance measure|single number]] to evaluate the models.

## Large data rationale
Assume that the features $x \in \mathbb{R}^n$ have enough information to predict $y$ accurately (e.g., a human expert could predict $y$). Then an algorithm with many parameters (low [[bias]] algorithm) together with a large data set (to reduce [[variance]]) should do well.