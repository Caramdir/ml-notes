# Ceiling analysis

Assume we have a machine learning problem that consists of $s$ steps in a pipeline.

For $1 \le n \le s$, compute the [[performance measure]], assuming that the first $n$ steps of the pipeline are 100% correct (i.e., manually feed the correct output of the first $n$ steps into step $n+1$).

This shows the best case gain when improving each module and helps to decide what to focus on.