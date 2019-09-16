---
title: Disributed Algorithms - Week 2
author: Jaan Tollander de Balsch - 452056
date: \today
---
## Exercise 2.2
Exercise 2.2 in @distributed_algorithms.

We can show that $2$-coloring a path with $n$ nodes takes $Ω(n)$ rounds, even if nodes are aware of $n$ (and their own unique identifiers).

This stems from the fact that the knowledge of $n$ doesn't inform the nodes about their relative position in the path.

The only information that can be derived from $n$ is whether the end nodes should have same color (odd $n$) or different color (even $n$). 

Unfortunately, the end nodes running a distributed algorithm cannot know which color the other end node has picked, without communicating the information along the path, which takes $O(n)$ rounds.

## References
