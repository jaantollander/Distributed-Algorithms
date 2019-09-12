---
title: Disributed Algorithms - Week 1
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

## References
