---
layout: lecture
title: Lecture 6&#58; Hamiltonian cycles
comments: True
---


Definition
====

A graph $$\Gamma$$ is *Hamilton* if there exists a closed walk that visits every vertex exactly once.



Although the definition of a Hamiltonian graph is extremely similar to an Eulerian graph, it is much harder to determine whether a graph is Hamiltonian or not: doing so is an NP-complete problem.



Examples
===



Proposition
===

The Petersen graph is *not* Hamiltonian.

Proof
===

Suppose the Petersen graph was Hamiltonian, and let $$v_1-v_2-v_3-\cdots-v_{10}-v_1$$ denote the Hamiltonian cycle.

The Petersen graph has 15 edges, and the Hamiltonian cycle uses 10 of them, so there must be 5 edges left in the Petersen graph that are not in the Hamiltonian cycle.  The proof works by considering the possibilities for these 5 extra edges.

Since the Petersen graph has no loops or multiple edges, none of these edges can go from a vertex to itself.  Since it has no triangles or 4 cycles, none of these extra edges can skip 1 or 2 vertices in the Hamiltonian cycle.  Thus, the only possibility for these edges is that they skip 4 or 5 vertices (skipping more than 5 vertices is the same as skipping less vertices in the other direction). 

We now claim that at least one of these extra edges must skip 4 vertices.  If not, then every extra edge would skip 5 vertices.  Since each vertex has degree 3, there must be one extra edge through each of these vertices.  But this configuration has many four cycles -- for instance, $$v_1--v_2--v_7--v_6--v_1$$.  Since the Petersen graph does not have any 4 cycles, we see this cannot occur.

Relabeling our edges if necesary, we can make the extra edge that skips the 4 cycle be the edge $$v_1--v_5$$.  Now, consider the extra edge at $$v_6$$.  This cannot skip 5, because that would make it adjacent to $$v_1$$, which already has its extra edge.  Thus, it must skip 4, and be adjacent to either $$v_10$$ or $$v_2$$.  But since each of these are adjacent to $$v_1$$, it would create a 4-cycle: either $$v_1-v_5-v_6-v_{10}-v_1$$, or $$v_1-v_5-v_6-v_2$$.  $$\square$$


Partial results on Hamiltonian graphs
----

Although there is no complete characterisation of Hamiltonian graphs, there are several nice sufficient conditions for a graph to be Hamiltonian; 

Ore's Theorem
====

Let $$\Gamma$$ be a simple graph with $$n$$ vertices such that for any two nonadjacent vertices $$v$$ and $$w$$, we have $$\text{deg}(v)+\deg{w}\geq n$$.  Then $$\Gamma$$ is Hamiltonian.

Proof
===

We will give a proof by contradiction.  First, suppose that $$\Gamma$$ were a counterexample.  Adding edges to $$\Gamma$$ preserves the condition on the degrees, and so we may continually add edges to $$\Gamma$$ until adding any more would create a Hamiltonian cycle.  We will thus assume that $$\Gamma$$ is a counterexample with the maximal set of edges.  

The benefit of this is that such a $$\Gamma$$ must have a non-closed path that visits every vertex exactly once.  To see this, add one more edge $$e$$ to $$\Gamma$$ -- the resulting graph then has a Hamiltonian cycle, which must pass through $$e$$, deleting $$e$$ give the desired path.

Let $$v_1-v_2-\dots v_{n-1}-v_n$$ be the path visiting every vertex of $$\Gamma$$.  We will complete the proof by showing there exists an $$i\in 3,\cdots, n-1$$ so that $$v_1$$ is adjacent to $$v_i$$ and $$v_{n-1}$$ is adjacent to $$v_{i-1}$$.  This completes the proof because $$v_1-v_2-\cdots v_{i-1}-v_n-v_{n-1}-v_{n-2}-\dots v_i-v_1$$ is a Hamiltonian path.

The existence of such an $$i$$ follows from the pigeon hole principle.  Since $$v_1$$ and $$v_n$$ are not adjacent by supposition, the sum of their degrees is at least $$n$$.  Two edges incident to them are accounted for $$v_1-v_2$$, and $$v_{n-1}-v_{n-2}$$, so there must be at least $$n-2$$ other edges incident to $$v_1$$ or $$v_{n}$$.  Since $$\Gamma$$ is simple, any such edge out of $$v_1$$ has $$n-3$$ possibilities:  $$v_3, v_4, \dots, v_{n-1}$$.  Similarly, there are $$n-3$$ possibilities for an edge adjacent to $$v_n$$ -- $$v_2,v_3,\dots, v_{n-2}$$.  We pair these edges up into the possibilities we want, creating $$n-3$$ bins.  Since there are $$n-2$$ edges we need to distribute among these bins, one of the bins must contain at least two, which is exactly what we needed to show.








