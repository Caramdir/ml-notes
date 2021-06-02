---
alias: performance measures, satisficing, satisficing metric, optimizing metric, satisficing and optimizing metrics
---
# Performance measures

Performance measures are used to [[evaluating a hypothesis|evaluate the hypothesis]] of a machine learning model or aid in [[model selection]]. 

Possible performance measures include:
- The cost function of the model (without regularization, i.e., with regularization parameter $\lambda = 0$).
- [[classification accuracy]]
- [[precision and recall]]
- [[F1 score|$F_1$ score]]

One should distinguish between *satisficing* and *optimizing* metrics. That is, one maximizes/minimizes the optimizing metrics,subject to the satisficing metrics being within certain bounds. Ideally one only has one optimizing metric

For example, accuracy could be an optimizing metric, while running time could be a satisficing one.