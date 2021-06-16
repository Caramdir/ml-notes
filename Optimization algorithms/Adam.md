# Adam
The *Adam* (short for *adaptive moment estimation*) optimization algorithm is a combination of [[gradient descent with momentum]] and [[RMSProp]].  [[@kingmaAdamMethodStochastic2017]]

Thus, after initializing $v_{\nabla J} = s_{\nabla J} = 0$, on each iteration $t$ the following steps are 
(where the squaring and root operations are component-wise):
$$
	\begin{aligned}
		v_{\nabla J} & \leftarrow \beta_1 v_{\nabla J} + (1-\beta_1) \nabla J \\
		s_{\nabla J} & \leftarrow \beta_2 s_{\nabla J} + (1-\beta_2) (\nabla J)^2 \\
		v_{\nabla J}^{cor} & \leftarrow \frac{v_{\nabla J}}{1 - \beta_1^t}\\
		s_{\nabla J}^{cor} & \leftarrow \frac{s_{\nabla J}}{1 - \beta_2^t}\\
		\theta & \leftarrow \theta - \alpha \frac{v_{\nabla J}^{cor}}{\sqrt{s_{\nabla J}^{cor}} + \epsilon}
	\end{aligned}
$$
The learning rate $\alpha$ is a [[hyperparameter]] that needs to be tuned, for the other parameters one usually keeps the values suggested by the authors: $\beta_1 = 0.9$, $\beta_2 = 0.999$, $\epsilon = 10^{-8}$.