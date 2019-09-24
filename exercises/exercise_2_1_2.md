---
title: Distributed Algorithms - Week 2
author: Jaan Tollander de Balsch - 452056
date: \today
---
## Exercise 2.1
Exercise 2.1 in @distributed_algorithms.

### a)
The chapter 2.2.1 in @distributed_algorithms describes an algorithm for solving the 2-coloring in $O(n)$ time. The algorithm for counting the nodes in the path can be implemented similarly.

1) Determine the leader node. Both endpoints send their unique identifiers along the path. The one with the lowest unique identifier is selected as the leader. We'll call the end node with a higher unique identifier rear node.

2) The leader node starts the count from $1$ and sends the count to its neighbor. The neighbor increments the count and then sends it its neighbor, and this repeats until the count reaches the rear node.

3) Now, we'll propagate the results from the rear node to leader node such that every node will memorize it. This is done by sending the count from the rear node to its neighbor and then to its neighbor repeating until it reaches the leader node.

### b)
Similarly to the proof in @distributed_algorithms, chapter 2.2.2 that 2-coloring cannot be done in $o(n)$ time, we can show that counting nodes cannot be done in $o(n)$ time.

Using the same construction, but instead of coloring the nodes based, we have a function that returns a count of nodes based on the neighbors. Similarly, we arrive at a contradiction that two different length paths would have the same count of nodes proving the statement.


## Exercise 2.2
Exercise 2.2 in @distributed_algorithms.

We can show that $2$-coloring a path with $n$ nodes takes $Ω(n)$ rounds, even if nodes are aware of $n$ (and their unique identifiers). This follows from the fact that the knowledge of $n$ doesn't inform the nodes about their relative position in the path. The only information that can be derived from $n$ is whether the end nodes should have the same color (odd $n$) or a different color (even $n$).  However, the end nodes running a distributed algorithm cannot know which color the other end-node has picked, without communicating the information along the path, which takes $O(n)$ rounds.

We can modify the proof in @distributed_algorithms, chapter 2.2.2, such that instead of coloring the nodes only based on their neighbors it also used the information about the path length. Let's denote the deterministic coloring function 

$$
f(𝐱, n)
$$

where $𝐱$ are the neighbors and $n$ is the path length.

For the two paths with lengths $2k$ and $2k+1$ there are two distinct cases:

1) If $f(𝐱, 2k)=f(𝐱, 2k+1)$ the proof reduces to the original proof.

2) If $f(𝐱, 2k)≠f(𝐱, 2k+1)$ the proof also end up in the with contradiction as the original proof.


## References
