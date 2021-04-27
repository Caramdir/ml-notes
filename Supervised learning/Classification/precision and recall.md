---
alias: precision, recall, true positive, false positive, true negative, false negative
---
# Precision and recall

If in a [[00 - classification problem]] some classes are more common than others, then [[classification accuracy]] is not a good measure for performance. For example the model might just never predict the uncommon class.

Let $y=1$ be the rare class we want to predict. 

- A correct prediction of $y = 1$ is a *true positive*.
- A wrong prediction of $y = 1$ is a *false positive*.
- A correct prediction of $y = 0$ is a *true negative*.
- A wrong prediction of $y = 0$ is a *false negative*.

*Precision* is the ratio
$$
	\frac{\text{true positives}}{\text{total predicted positives}} =
	\frac{\text{true positives}}{\text{true positives} + \text{false positives}}.
$$
*Recall* is the ratio
$$
	\frac{\text{true positives}}{\text{actual positives}} =
	\frac{\text{true positives}}{\text{true positives} + \text{false negatives}}.
$$

One way to trade off between precision and recall is to change the probability (i.e., the output of the hypothesis) above which a positive result is predicted.

The harmonic mean of precision and recall is the [[F1 score|$F_1$ score]].