---
alias: sigmoid function, sigmoid
---
# Logistic function

The logistic function is one example of a sigmoid function, that is,  a bounded, differentiable, real function which is defined for all real input values and has a non-negative derivative at each point and exactly one inflection point^[https://en.wikipedia.org/wiki/Sigmoid_function]. The [[Coursera course on machine learning]] refers to the logistic function as *the* sigmoid function.

The logistic function is given by
$$
	g(z) = \frac{1}{1+e^{-z}}.
$$
Its derivative is
$$
	g'(z) = g(z)(1-g(z)).
$$