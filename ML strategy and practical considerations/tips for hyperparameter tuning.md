---
alias: hyperparameter tuning
---
# [[hyperparameter|Hyperparameter]] tuning

- Try random values, don't use a grid: it is difficult to know in advance which hyperparameters are important. Random sampling gives different values for each parameter on each try, and hence in particular also for the important ones.
- Coarse to fine sampling scheme: After a first round of sampling, focus on a smaller region with the best values and do a finer search there.
- For real valued hyperparamters with a large (relative) scale, sample logarithmically: take $10^r$ with $r$ chosen uniformly from an appropriate interval.
- For the parameter $\beta$ of [[exponentially weighted averages]], sample $1-\beta$ instead: e.g. instead of $0.0 \le \beta \le 0.999$ instead look at $0.001 \le 1-\beta \le 0.1$ and sample that logarithmically.
- Re-test hyperparameters occasionally.
- There are two schools of thought:
	1) Babysit one model: change hyperparameters while model is training over multiple days.
	2) Train many different models in parallel.
	
	The correct approach depends on the amount of available computational resources.