---
alias: exponentially weighted moving averages
---
# Exponentially weighted (moving) averages

A method for smoothing out noisy data $\theta_i$. For a fixed parameter $\beta \in (0,1)$ one sets $v_0 = 0$ and recursively
$$
	v_t = \beta v_{t-1} + (1-\beta)\theta_t.
$$
This has the effect of averaging over the last $
\approx \frac{1}{1-\beta}$ values (as $\beta^{1-\beta} \approx e^{-1}$, so after this time the weight for a given data point is $< \frac13$).

This is computationally and memory-wise more efficient than just taking the averages over the last data values.

Since $v_0 = 0$, the first few values are biases towards $0$. Thus one can do a *bias correction* and use
$$
	\frac{v_t}{1-\beta^t}
$$
instead.