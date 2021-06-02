# Error analysis

*Error analysis* is the idea of of examining examples if the [[cross-validation set|cv set]] which have been misclassified. This way one sees the examples which are most difficult for the model and might spot some trends which suggest how to improve the model.

One way to do so is to see what percent of misclassified data is of a certain type and to classify error types in manually evaluated data. This way one knows which type of error to focus on.

## Mislabled data

One may also find that there are mislabled examples in the training/test data.

[[Deep learning]] algorithms are usually quite robust to random errors in the training set (though less robust to systematic errors).

To evaluate the impact of mislabeled data in the [[cross-validation set|dev set]] and [[test set]], check what percentage of errors is due to wrong labels in the data. If one decides to fix the mislabeled data, one has to be careful to apply the same procedure to both the dev and test set. One might also consider to examine the examples the algorithm got right for mislabeled data.

