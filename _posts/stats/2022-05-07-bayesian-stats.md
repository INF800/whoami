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

1. L1 Background 📚

    - Rules of Probability 📐
    - Odds 😨
    - Expectations 💣


<div class="divider"></div>


## 📚 L1 Background

Required beginner-level foundations to undertand probability theory.

### 📐 Rules of Probability

Every *event* has *probability* associated with it.

> An *event* is written in captial letter. If $$X$$ is probability of a coin falling with heads ($$H$$) or tails ($$T$$), we can represent it as
> $$
> \begin{align}
> P(X  &= H) &= \frac{1}{2} \tag{1} \label{eq:heads} \\
> P(X  &= T) &= \frac{1}{2} \tag{2} \label{eq:tails} \\
> \end{align}
> $$
>
> **Note:** $$P(X=T)$$ can also be written as $$P(T)$$

Probabilites of all possible *events* must add upto 1. As a consequence, individual probabilities must always lie between 0 & 1. Similarly, *complement of an event A* i.e probability of it not happening is $$1 - P(A)$$

> Sum of $$\eqref{eq:heads}$$ and $$\eqref{eq:tails}$$ is $$1$$ because we are assuming that there is not other event that is possible for a coin toss *event*.
> 
> Both $$ \eqref{eq:heads}$$ and $$\eqref{eq:tails}$$ both are $$\in [0, 1]$$
> 
> $$ \sum_{i=0}^{n} P(X=i) = 1 \tag{3} $$
> 
> $$ P(A^{c}) = 1 - P(A) \tag{4} $$

If events A and B are dependant, $$P(A\cup B) = P(A) + P(B) - P(A\cap B)$$. And If they are mutually exclusive, $$P(A\cup B) = P(A) + P(B)$$. 

Have a look at three events formula.

<!-- $$
\begin{align}
P(A \cup B \cup C) = P(A) + P(B) + P(C) − P(A \cap B) − P(A \cap C) − P(B \cap C) + P(A \cap B \cap C)
\end{align}
$$ -->

> If mutually exclusive, $$P \left( \bigcup_{i=1}^{n} A_{i} \right) = \sum_{i=1}^{n} P(A_{i}) $$
>
> **Note:** This is called inclusion / exclusive fomula. $$\cup$$ and $$\cap$$ denote "or" and "and" respectively.

**Type** | **Mutually Exclusive Events** | **Independant Events** 
--- | --- | ---
**Occurance** | ❌ Simultaneously | ✅ Simultaneously
**Influence** | ✅ Dependant | ❌ In-dependant |
**Example** | If A occurs, B will not occur. | If A occurs, B may or may not occur 

> Mutually exclusive events A and B 
> $$P(A\cap B) = 0$$ 
> ![mute](assets/blogs/bstats/mut-exclusive.png) 
>
> Independant events A and B
> $$P(A\cap B) = P(A)\dot P(B)$$
> ![indep](assets/blogs/bstats/indep.png)
>
> We will cover inependant events later.

<div class="divider"></div>

### References

[^1]: Link to set of courses: https://www.coursera.org/learn/bayesian-statistics