---
title: Distributed Algorithms - Week 4
author: Jaan Tollander de Balsch - 452056
date: \today
---
# Exercise 4.1
Exercise 4.1 in @distributed_algorithms.

We denote port-numbered network as a triple $N=(V,P,p)$, where $V$ is the set of nodes, $P$ is the set of ports, and $p:P→P$ is a functions that specifies the connections between the ports. Each port is a pair $(v,i)$ where $v∈V$ and $i∈\{1, 2, ...\}.$ [@distributed_algorithms, chapter 4.2]

---

The BMM algorithm consists of the following sets:

- Execution states $S=\{UR, MR(i), US, MS(i)\}$
  - Initial value $UR$
  - Stotting execution states $S_{out}=\{US, MS(i)\}⊆S$
- Colors $C=\{white,black\}$
  - Initial value is given by given $2$-coloring function $f:V→C$.
- Variable $M(v)∈M=\mathcal{P}(\{1, 2, ..., \deg(v)\})$
  - Initial value $M(v)←∅$
- Variable $X(v)∈X=\mathcal{P}(\{1, 2, ..., \deg(v)\})$
  - Initial value $X(v)←\{1, 2, ..., \deg(v)\}$
- Iteration $k∈K=\{1, 2, ...\}$
  - Initial value $1$
- Messages $\{proposal, matched, accept\}$

Note that we denote the whole set of variables $M(v)$ and $X(c)$ with just their symbols $M$ and $X$. Also, $\mathcal{P}(⋅)$ denotes the powerset.

---

The BMM algorithm formalized as a state machine.

The set of inputs consists of the $2$-coloring function
$$
\mathrm{Input}_A = \{f\}
$$

The set of states consists of $5$-tuples of the value of the execution state, color, variable $M(v)$, variable $X(v)$ and iteration $k$
$$
\mathrm{States}_A = S × C × M × X × K
$$

Output states restrict the execution states to the stopping states
$$
\mathrm{Output}_A = S_{out} × C × M × X × K ⊆ \mathrm{States}_A
$$

The set of messages is otherwise the same, but we also add $nomsg$ into the set
$$
\mathrm{Msg}_A = \{proposal, matched, accept, nomsg\}
$$

The initialization function $\mathrm{init}_{A,d}(f) : \mathrm{Input}_A → \mathrm{States}_A$ return the state tuple with the initial values
$$
\mathrm{init}_{A,d}(f) = (UR, f(v), ∅, \{1, 2, ..., \deg(v)\}, 1)
$$

Send function $\mathrm{send}_{A,d} : \mathrm{States}_A→\mathrm{Msg}_A^d$ constructs the outgoing message as follows:

$\mathrm{send}_{A,d}(s, c, m, x, k)$

1) $msg=[nomsg_1,nomsg_2,...,nomsg_{\deg(v)}]$ (define the message vector)
1) If $isodd(k)$ and $c = white$ 
2) ... if $s = UR$ and $k≤\deg_N(v)$: 
3) ... ...$msg[k]=proposal$
4) ... if $s = MR(i)$: 
5) ... ...$msg[i]=matched,∀i=\{1,2,...,\deg(v)\}$
6) If $iseven(k)$ and $c = black$ 
7) ... If $s=UR$ and $M(v)≠∅$
8) ... ... $msg[\min m]=accept$
9) return $msg$

The receive function $\mathrm{receive}_{A,d}:\mathrm{States}_A×\mathrm{Msg}_A^d→\mathrm{States}_A$ processes incoming messages as follows:

$\mathrm{receive}_{A,d}((s, c, m, x, k), msg)$

1) $s_{new}=(undef,c,undef,undef,k+1)$ (initialize new state vector)
2) For $msg'∈msg$ (iterate over the messages)
3) ... If $isodd(k)$ and $c = white$ 
4) ... ... If $s=UR$ and $k>\deg(v)$
5) ... ... ... $s_{new}.s = US$
6) ... If $isodd(k)$ and $c = black$
7) ... ... If $s=UR$
8) ... ... ... If $msg'=matched$: $s_{new}.x=x(v)∖\{i\}$
9) ... ... ... If $msg'=proposal$: $s_{new}.m=m(v)∪\{i\}$
10) ... If $iseven(k)$ and $c = black$ 
11) ... ... If $s=UR$ and $m≠UR$: $s_{new}.s=MS(i), i=\min m$
12) ... ... If $s=UR$ and $m=UR$: $s_{new}.s=US$
13) ... If $iseven(k)$ and $c = white$ 
14) ... ... If $s=UR$ and $msg'=accept$: $s_{new}.s=MR(i)$
15) return $s_{new}$


# References
