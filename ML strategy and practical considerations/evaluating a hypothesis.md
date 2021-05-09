# Evaluating a hypothesis

The performance of a hypothesis on the [[training set]] is not indicative to its performance on new data, e.g., because of [[variance|overfitting]]. Thus one splits the data into two portions, the [[training set]] and the [[test set]]. 

In the [[Coursera course on machine learning]], a split of 70%/30% is suggested. It is important to assign data to the sets randomly.

On then uses the training set to create the model and the test set to evaluate how well the model generalizes. For this it is important to consider useful [[performance measure|performance measures]].