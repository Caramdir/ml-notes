---
alias: recommender system
---
# Recommender system

Given a number of users who have rated some items, predict the ratings of users to items they did not rate.

Notation:
- $n_u$ - the number of users
- $n_i$ - the number of items
- $r(i,j)$, which is one if user $j$ has rated item $i$.
- $y(i,j)$, the rating given by user $j$ to item $i$.

The goal is to predict missing values in $y$.

## Algorithms

- [[content based recommendations]]
- [[collaborative filtering]]