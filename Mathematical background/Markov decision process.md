# Markov decision process

A *Markov decision process* consists of the following data:

- A set of *states* $S$, called the *state space*.
- A set of *actions* $A$, called the *action space*.
- Probabilities $P_a(s, s')$, that if action $a$ is taken at state $s$, the state at the next time step is $s'$. That is, $P_a(s, s') = \mathbb P(s_{t+1} = s' \mid s_t = s,\ a_t = a)$.
- (Expected) immediate rewards $R_a(s, s')$ after transitioning from state $s$ to $s'$ due to action $a$.

A *policy function* is a (possibly probabilistic) function $\pi\colon S \to A$. Thus a policy function fixes the action at each step.

The usual optimization problem for Markov decision processes is to find a policy function that maximizes cumulative expected reward
$$
\mathbb E\Bigl[\sum_y \gamma^t R_{a_t}(s_t,\, s_{t+1})\Bigr],
$$
where $a_t = \pi(s_t)$, $s_{t+1} \sim P_{a_t}(s_t,\, s_{t+1})$, and $0 < \gamma \le 1$ is a discount factor (usually close to 1). A policy that maximizes this expected value is called an *optimal policy* and denoted $\pi^*$.