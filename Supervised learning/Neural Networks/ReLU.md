---
alias: leaky ReLU
---
# Rectified linear unit

The ReLU function (short for *rectified linear unit*) is defined by
$$
	\operatorname{ReLU}(z) = \max(0,z)
$$
with derivative
$$
	\operatorname{ReLU}(z) = 
	\begin{cases}
		0 & \text{if } z < 0, \\
		1 & \text{if } z \ge 0.
	\end{cases}
$$
We note that here at $z=0$ we use the right derivative.

A variant of ReLU us *leaky ReLU*, which is $\max(cz,\, z)$ for some small positive constant $c$ (e.g. $c=0.01$).