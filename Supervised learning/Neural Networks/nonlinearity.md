---
alias: activiation, activiation function
---
# Nonlinearity

If all nodes in a [[00 - neural networks|neural network]] compute affine functions, then the whole network collapses to a single affine function. Thus in each node (except possibly in the last layer) one needs to apply a nonlinear function to the output of the affine function. This function is called a *nonlinearity* or an *activiation function.*

Frequent choices include sigmoid functions such as the [[logistic function|logistic]] and [[tanh]] functions and the [[ReLU]] function.

In deep neural networks, sigmoid functions are discouraged as they have small gradients away from the origin making learning slow.