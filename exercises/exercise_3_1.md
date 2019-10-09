---
title: Distributed Algorithms - Week 3
author: Jaan Tollander de Balsch - 452056
date: \today
---
# Exercise 3.1
Exercise 3.1 in @distributed_algorithms.

<!-- TODO: vice versa!!! -->

Let $G=(E,V)$ be a graph. Let $I⊆V$ and define $C=V∖I$.

## (a)
Let $I$ be an independent set, that is, each edge $e∈E$ has at most one endpoint in $I$:

1) If edge $e∈E$ has zero endpoints in $I$ it implies that both endpoints are in $C.$
2) If edge $e∈E$ has one endpoint in $I$ it implies that the other endpoint is in $C.$

Therefore, each edge has at least one endpoint in $C$ which implies that $C$ is a vertex cover.

## (b)
Let $I$ be a maximal independent set. Section (a) proves that $C$ is a vertex cover. It's left to prove that the vertex cover is minimal. 

We can use proof by contradiction. Lets start by assuming  that $C$ is not minimal vertex cover. Then there is a vertex $u∈C$ such that all of its neighbors are in $C$. However, this is contradiction because if vertex $u$ doesn't belong to the independent set $I$, its not maximal.

## (c)
Let $I$ be maximum independent set of cardinality $|I|.$  Sections (a) and (b) prove that $C$ is minimal vertex cover of cardinality $|C|=|V|-|I|.$ If $C$ is not minimum vertex cover, there exists vertex cover $C'$ with cardinality $|C'|<|C|$. However, this implies that there exists independent set $|I'|$ with cardinality $|I'|=|V|-|C'| > |V|-|C| = |I|$ which is a contradiction. Therefore, $C$ is a minimum vertex cover.

## (d)
Let $C$ be $2$-approximation of minimum vertex cover. Therefore, $I$ is the corresponding independent set. 

Lets assume that $I$ is $2$-approximation of maximum independent set. Then, by definition, for all independent sets $I'⊆V$ where $C'=V∖I$ is the correspoding vertex cover, we have

$$
\begin{aligned}
2|I|&≥|I'| \\
2(|V|-|C|)&≥|V|-|C'| \\
2|C|&≤|V|+|C'| \\
\end{aligned}
$$

We should have $|C|≤2|C'|$ because $2$-approximation of minimum vertex cover.
$$
\begin{aligned}
|C|&≤2|C'| \\
2|C|&≤4|C'| \\
|V|+|C'| &≤ 4|C'| \\
|V| &≤ 3|C'| 
\end{aligned}
$$
Doensn't hold for all $C'$ implies contradiction.

<!-- Since $|V|≥|C'|$ we have that 

$$
(1-\frac{1}{α})|V|+\frac{1}{α}|C'| ≥ α|C'| \\
(1-\frac{1}{α})|V| ≥ (α-\frac{1}{α})|C'|
$$

which doensn't quarantee -->

---

<!-- Then by definition, for all vertex covers $C'⊆V$ where $I'=V∖C'$ is the corresponding independent set, we have
$$
\begin{aligned}
|C|&≤α|C'| \\
|V|-|I|&≤α(|V|-|I'|) \\
-|I|&≤α|V|-|V|-α|I'| \\
|I|&≥(1-α)|V|+α|I'| \\
|I|+(α-1)|V|&≥α|I'|, ∣ |V|≥|I|
\end{aligned}
$$

$I$ is $α$-approximation of maximal independent set if  -->


## (e)


<!-- # Exercise 3.2
Exercise 3.2 in @distributed_algorithms.

## (a)
## (b)
## (c)
## (d) -->

# References
