---
title: Distributed Algorithms - Week 1
author: Jaan Tollander de Balsch - 452056
date: \today
---
## Exercise 1.3
Exercise 1.3 in @distributed_algorithms. 

Distributed 3-coloring for an undirected path. The algorithm is applied iteratively on the nodes.

---

Apply `P3CBit` to the node such that the neighbor with a higher unique identifier is considered as its successor. 

If the node has two neighbors with higher unique identifier it's local minima and its successor can be chosen at random. 

If the node is a local maximum, i.e. it has no neighbors with a higher unique identifier, we don't apply `P3CBit`. Instead, if the colors of the neighbors are in the stopping states, we choose a color from the stopping states for the node such that it's different from its neighbors' colors, otherwise we do nothing.

---

## Exercise 1.4
Exercise 1.4 in @distributed_algorithms.

Using a similar algorithm and analysis as in chapter 1.5.1 we can make a randomized algorithm that colors the nodes with unique colors with high probability. Then we'll use `P3CBit` (one that works on undirected paths) to reduce the coloring into 3-coloring.

Draw a color randomly for each node from the discrete uniform distribution from $1$ to $m$ where $m≥3$. If any of the neighbors have the same color draw the color again. The probability that node $u$ will stop after an iteration is at least
$$1-2/m.$$

Fix a positive constant $C$. Run the algorithm for
$$k=(C+1)\log_{m/2}n$$

steps, where $n$ is the number of nodes in the network. The probability that a node has stopped after $k$ iterations is 
$$(1-(1-2/m))^k=(2/m)^k=1/(n^{C+1}).$$

Probability that all nodes have stopped after $k$ iterations
$$1-n⋅1/(n^{C+1})=1-1/n^C.$$

As we increase $m$ the number number of iterations $k$ required for the coloring decreases. Since `P3CBit` runs $O(\log^*(n))$ steps we can choose large enough $m$ assuming that $n$ is known constant that required iterations $k$ becomes close to $1$, without adding many iterations to `P3CBit`. Therefore the total runtime remains $O(\log^*(n))$.


## References
