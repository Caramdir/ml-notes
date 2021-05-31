# Gradient descent with momentum

Depending on the shape of the function, [[gradient descent|gradient descent]] may oscillate and thus slow down convergence. One can use [[exponentially weighted averages]] to dampen the oscillation and smooth out gradient descent.

Set $v_{\nabla J} = 0$. In each iteration of [[gradient descent]] first compute the gradient $\nabla J$ as usual (e.g. on the current [[mini-batch gradient descent|mini-batch]]). Then set
$$
	v_{\nabla J} = \beta v_{\nabla J} + (1-\beta)\nabla J
$$
and use this to update the parameters:
$$
	\theta = \theta - \alpha v_{\nabla J}.
$$
The value of $\beta$ is a new [[hyperparameter]]. A common value is $\beta = 0.9$.

In practice one does not use bias correction, as after a few iterations it does not have any effect.

Sometimes
$$
	v_{\nabla J} = \beta v_{\nabla J} + \nabla J
$$
is used instead, but not that the missing $(1-\beta)$ term impacts the learning rate $\alpha$.