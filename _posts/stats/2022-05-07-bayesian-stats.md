---
title: Bayesian Statistics - Part I
updated: 2022-05-0 23:37
category: 
- Statistics
---

> 🤐 Draft version

## Acknowledgements

> Heavily relies on bayesian statistics specialisation by University of California, Santa Cruz [^1].

>  *"The theory of probabilities is basically just common sense reduced to calculus; it makes one appreciate with exactness that which accurate minds feel with a sort of instinct, often without being able to account for it."* --Pierre-Simon Laplace

<div class="divider"></div>

# Contents

1. L1 Background
    1.1 Rules of Probability
    1.2 Odds
    1.3 Expectations


<div class="divider"></div>


## 1. L1 Background

Required beginner-level foundations to undertand probability theory.

### 1.1. Rules of Probability

- Every *event* has *probability* associated with it.

    >  *Event* is written in captial letter. If $$X$$ is probability of a coin falling with heads ($$H$$) or tails ($$T$$), we can represent it as
    > $$
    > \begin{align}
    > P(X  &= H) &= \frac{1}{2} \tag{1} \label{eq:heads} \\
    > P(X  &= T) &= \frac{1}{2} \tag{2} \label{eq:tails} \\
    > \end{align}
    > $$

- Probabilites of all possible *events* must add upto 1. As a consequence, individual probabilities must always lie between 0 and 1.

> - Sum of $$\eqref{eq:heads}$$ and $$\eqref{eq:tails}$$ is $$1$$ because we are assuming that there is not other event that is possible for a coin toss *event*.
> - $$\eqref{eq:heads}$$ and $$\eqref{eq:tails}$$ both are $$\in [0, 1]$$

<div class="divider"></div>

### References

[^1]: Link to set of courses: https://www.coursera.org/learn/bayesian-statistics