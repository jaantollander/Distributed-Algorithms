# Exercise 2
Pseudocode:

---

1) Let $I$ be the set of active neighbors (unique identifiers).
2) Initialize the set of colors of inactive members $N=∅$.

*Repeat until break*

1) Send message $c$ to all active neighbours $I$.
2) Receive messages from all active neighbours. Let $M$ be the set of messages received.
3) Remove inactive members from the set of active members, i.e. those who sent message with value in $\{1,2,3\}$ and add the messages to set $N$.
4) If $c∈\{1,2,3\}$ (stopping state is reached)
5) * Break the loop
6) If $c∉\{1,2,3\}$ and $c>\max (M∪N)$: 
7) * Let $c←\min(\{1,2,3\}∖(M∪N))$.

--- 
