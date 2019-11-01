---
title: Distributed Algorithms - Week x
author: Jaan Tollander de Balsch - 452056
date: \today
---
# Exercise 7.2
Exercise 7.2 in @distributed_algorithms.

Let $A$ be an algorithm that labels each node in graph $G=(V,E)$ with unique label with high probability. Let $n=|V|$ be the number of nodes. Each node draws a label uniformly at random (with replacement) from the set of labels $\{1,...,m\}$ where $m=n^C$ and $C>0.$ The probability that each node draws an unique label is
$$
\begin{aligned}
\frac{m-0}{m} ⋅ \frac{m-1}{m} ⋅ ... ⋅ \frac{m-(n-1)}{m} &≥ \frac{(m-(n-1))^n}{m^n} \\
&≥ \frac{(m-n)^n}{m^n} \\
&= \left(1-\frac{n}{m}\right)^n \\
&= \left(1-\frac{1}{n^{C-1}}\right)^n
\end{aligned}
$$
For any $c>0$ we can choose large enough $C>0$ such that
$$
\left(1-\frac{1}{n^{C-1}}\right)^n ≥ 1 - \frac{1}{n^c}.
$$
Therefore, *with high probability* in one round, the algorithm can find unique labels for each node.


# Exercise 7.3
Exercise 7.3 in @distributed_algorithms.

Let $G=(V, E)$ be any graph of maximum degree $Δ$. Then the `PN` algorithm $A$ outputs an independent set $I$ of expected size $|V|/O(Δ)$ in $O(1)$ rounds.

As seen in exercise 7.3, nodes in PN-model can be labeled with unique labels (identifiers) with high probability in $O(1)$ rounds. Using these labels each node can determine whether its local maxima in one round. Nodes that are local maxima are included in the independent set $I$. Also, all isolated nodes are included in $I$. Therefore, algorithm $A$ finds an independent set $I$ in $O(1)$ rounds.

Expected size $|V|/O(Δ)$ of the independent set $I$ is shown as follows:

1) *The size $I$ is directly correlated to the number of nodes $|V|$.*
   * When there are more nodes in $G$, the can independent sets can be larger. 

2) *The size $I$ is inversely correlated to the maximum degree $Δ$.* 
    * Let $G'$ be a graph with the maximum degree of $Δ$. Then algorithm $A$ will find an independent set $I'$.
    * Let $G''$ be a graph created by adding an edge to $G'$ such that the maximum degree of $G''$ is $Δ+1$. Then algorithm $A$ will find independent set $I''$.
    * Then we'll have $|I''|≤|I'|$ because if the edge was added between two nodes in $I'$ only one of them can be in $I''$. Hence the expected size of the independent set decrease as $Δ$ increases.


# References
