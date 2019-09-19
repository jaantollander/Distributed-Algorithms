---
title: Disributed Algorithms - Week 2
author: Jaan Tollander de Balsch - 452056
date: \today
---
## Exercise 2.1
Exercise 2.1 in @distributed_algorithms.

### a)
The chapter 2.2.1 in @distributed_algorithms describes an algorithm for solving the 2-coloring in $O(n)$ time. The algorithm for counting the nodes in the path can be implemented similarly.

1) Initialize front and rear nodes, i.e. end nodes with highest and lowest unique identifier

2) The front node starts the count from $1$ and sends the count to its neighbour. The neighbour increments the count and then sends it its neighbor, and this repeats until the count reaches the read node.

3) Now, we'll propagate the results from rear node to front node such that every node will memorize it. This is done by sending the count from rear node to its neighbour, and then to its neighbor repeating until it reaches the front node.

### b)
Similarly to the proof in @distributed_algorithms, chapter 2.2.2 that 2-coloring cannot be done in $o(n)$ time, we can show that counting nodes cannot be done in $o(n)$ time.

Using the same construction, but instead of coloring the nodes based, we have a function that return a count of nodes based on the neighbors. Similarly, we arrive at a contradiction that two different length paths would have the same count of nodes proving the statement.


## Exercise 2.2
Exercise 2.2 in @distributed_algorithms.

We can show that $2$-coloring a path with $n$ nodes takes $Ω(n)$ rounds, even if nodes are aware of $n$ (and their own unique identifiers).

This stems from the fact that the knowledge of $n$ doesn't inform the nodes about their relative position in the path.

The only information that can be derived from $n$ is whether the end nodes should have same color (odd $n$) or different color (even $n$). 

Unfortunately, the end nodes running a distributed algorithm cannot know which color the other end node has picked, without communicating the information along the path, which takes $O(n)$ rounds.

---

<!-- $O(n)$ algorithm cousld also count the nodes when establishing leader, but the algorithm wouldn't be faster -->

Following the proof in @distributed_algorithms, chapter 2.2.2. 

coloring(neighbors)

coloring(neighbors, length), coloring function has knowledge of the length of the path

lengths: $2k$, $2k+1$
  
- if coloring outputs same for same neighbors -> original problem
- if coloring outputs different for same neighbors -> 


## References
