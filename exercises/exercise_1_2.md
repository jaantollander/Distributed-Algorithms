---
title: Disributed Algorithms - Week 1
author: Jaan Tollander de Balsch - 452056
date: \today
---
## Exercise 1.2
Exercise 1.2 in @distributed_algorithms.

Pseudocode implementation of the greedy algorithm such that stopped nodes do not send messages. The general idea is that the algorithm repeats the loop once more after it has reached the stopping state informing other nodes and then breaks the loop. Each node also memorizes the set of active neighbors and the colors of inactive neighbors. Otherwise, the algorithm is similar to the one described in chapter 1.3.

---

1) Let $I$ be the set of active neighbors (element are unique identifiers).
2) Initialize the set of colors of inactive members $N=∅$.
3) Let $c$ be the color of the node.

*Repeat until break*

1) Send message $c$ to all active neighbours $I$.
2) Receive messages from all active neighbours. Let $M$ be the set of messages received.
3) Remove inactive members from the set of active members, i.e. those who sent message with value in $\{1,2,3\}$ and add the messages to set $N$.
4) If $c∈\{1,2,3\}$ (stopping state is reached)
5) * Break the loop
6) If $c∉\{1,2,3\}$ and $c>\max (M∪N)$: (stopping state is not reached and $c$ is the local maximum)
7) * Let $c←\min(\{1,2,3\}∖(M∪N))$.

--- 

## References
