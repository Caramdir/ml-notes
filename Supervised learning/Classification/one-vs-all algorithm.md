---
alias: one-vs-all, one-vs-rest, one-vs-rest algorithm
---
# One-vs-all algorithm

The *one-vs-all* (or *one-vs-rest*) algorithm is a way to turn any binary classifier into a multiclass classifier.

For each class $i$, one trains a binary classifier $h^{(i)}(x)$ to decide between class $i$ and all other classes. Thus one interpretes $h^{(i)}(x)$ as the probability that $y = i$ given $x$.

To make a prediction, one runs all classifiers and picks $i$ with the highest value for $h^{(i)}(x)$.