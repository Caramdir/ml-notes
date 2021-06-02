# Multi-task learning

If one network is trained simultaneously for several tasks, this is called *multi-task learning*. For example, a network may assign multiple labels at once to some data. In this case the output is a vector with values in {0,1} and the cost function is
$$
	\frac1m \sum_{i=1}^m \sum_j \mathcal L(\hat y_j, y_j)
$$
where $\mathcal L$ us usually [[binary classification|logistic loss]]. If some labels are unkown, one only takes the sum over the known labels.

This is useful when the tasks share low-level features and the amount of available data for each tasks is roughly the same. This is of course predicated on the assumption that one can train a large enough network to do well on all the tasks.