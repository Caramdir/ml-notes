---
alias: Bayes error, Bayes optimal error, avoidable bias
---
# Bayes error and human level performance

The *Bayes optimal error* (or simply *Bayes error*) is the lowest theoretically possible error rate on a problem. Thus performance on a given task can never be better than Bayes error.

[[Andrew Ng]] calls the difference between the Bayes error and the actual error the *avoidable bias*. It is a measure of the best theoretical performance gain. 

- If the avoidable bias is high, then one should focus on reducing [[bias]].
- If the avoidable bias is small, then one should focus on reducing [[variance]], or working on other steps in a chain of tasks.

In practice, it is usually impossible to estimate the Bayes error for a problem. Thus one uses *human level performance* as a stand-in. Here the human level performance should be measured as the performance of (a group of) experts at the given task.

As long as the performance of an algorithm is worse than human level performance, it is relatively easy to make progress: one can get labeled data from humans, gain insight from [[error analysis]] and understands whether to focus on bias or variance. Once an algorithm surpasses human level performance it is much harder to make progress, and one does not know how much room there is for improvement.