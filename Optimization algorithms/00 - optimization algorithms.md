---
alias: optimization algorithm, epoch
---
# Optimization algorithm

An algorithm for finding an extremum of a given function. Most algorithms used in machine learning are variations on [[gradient descent]].

One pass over the training data with any of the following algorithms is called an *epoch*.

## Algorithms
- [[gradient descent]]
- [[stochastic gradient descent]]
- [[mini-batch gradient descent]]
- [[gradient descent with momentum]]
- [[RMSProp]]
- [[Adam]]
- [[learning rate decay]]

## The problem of local optima
The training process may get stuck in a local optimum. For deep learning algorithms this is however highly unlikely, as all second derivative would need to have the same sign, so that most critical points are saddle points instead.

## The problem of plateaus
A plateau is a region with  gradient close to $0$. It may take a long time to get of a plateau.