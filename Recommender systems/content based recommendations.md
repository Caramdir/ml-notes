# Content-based recommendations

A [[00 - recommender system]], where each item $i$ has a feature vector $x^{(i)}$ which is know a priori. 

The for each user $j$ learn parameters $\theta^{(j)}$ via linear regression on the items that user $j$ has rated. Predict user $j$ rating item $i$ with $(\theta^{(j)})^Tx^{(i)}$.