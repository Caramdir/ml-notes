# learning rate decay

The learning rate $\alpha$ in [[gradient descent]] and related [[00 - optimization algorithms|optimization algorithms]] can be slowly decreased during learning to obtain better convergence.. This is especially useful in [[mini-batch gradient descent|mini-batch]] to dampen out noise from the batches.

There are many different options of how to decrease the learning rate. In the following examples $t$ is the [[00 - optimization algorithms|epoch]] number.

- $\alpha = \frac{1}{1 + (\text{decay rate})t}\alpha_0$
- Exponential decay $\alpha = \gamma^t \alpha_0$ for some $0 < \gamma < 1$ (e.g. $\gamma = 0.95$).
- $\alpha = \frac{k}{\sqrt{t}}{\alpha_0}$ (or maybe using the mini-batch number instead)
- $\alpha = f(t)$ where $f$ is a discrete staircase function
- manual adjustment depending on current performance for long-running training
