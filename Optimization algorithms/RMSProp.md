# RMSProp

The *RMSProp* or (*root mean square propagation*) algorithm is a variant of [[gradient descent]] that reduces large components of the gradient vector.

In each iteration on first computes $\nabla J$ as usual (e.g on the current [[mini-batch gradient descent|mini-batch]]) and then sets
$$
	s_{\nabla J} = \beta_2 s_{\nabla J} + (1-\beta_2)(\nabla J)^2,
$$
where the squaring is done element-wise, and the updates the parameters with
$$
	\theta := \theta - \alpha\frac{\nabla J}{\sqrt{s_{\nabla J}} - \epsilon},
$$
where $\epsilon$ is there for numerical stability (e.g., $\epsilon = 10^{-8}$) and $\beta_2$ is a new [[hyperparameter]].

This has the effect of decreasing components of $\nabla J$ which are large, while not effecting small ones much. One can the use a larger learning rate.