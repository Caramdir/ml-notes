# Model selection

To select between different models for a given problem (e.g. the degree used in [[polynomial regression]]), on should not use the [[training set]] or the [[test set]]. If using the former, one does not obtain any information about generalization. If using the latter, the model is fitted to the test set, and one obtains less information about how the model generalizes to new data.

Thus one randomply splits the data into three subsets:
- the *[[training set]]*,
- the *[[cross-validation set]]* (also called *validation* or *cv* set),
- and the *[[test set]]*.

The training set is used to train the different models. The cross-validation set is used to compare the different models using [[performance measure|performance measures]] and choose a model. Finally, the test set is used to gauge performance of the chosen model on new data.

One aid in model selection are [[learning curves]].