---
layout: lecture
title: Lecture 2&#58; More examples, handshake lemma, Eulerian cycles
comments: True
---


Examples and types of graphs
---

A few basic examples
===

1. The *complete graph* $$K_n$$ has $$n$$ vertices, and each vertex is connected to every other vertex by exactly one edge (so $$K_n$$ is a simple graph)
2. The *empty graph* $$E_n$$ has $$n$$ vertices and no edges between them
3. The *path* $$P_n$$ consists of $$n$$ vertices, $$v_1,\dots, v_n$$, and $$n-1$$ edges, $$e_1,\dots, e_{n-1}$$, where $$e_i$$ connects $$v_i$$ with $$v_{i+1}$$
4. The *cycle graph* $$C_n$$ is obtained from the path $$P_n$$ by adding one edge, between $$v_n$$ and $$v_1$$
5. The *wheel* $$W_{n+1}$$ is obtained from the cycle $$C_n$$ by adding one more vertex $$v_0$$, and connecting to every edge in $$C_n$$
6. The *Petersen graph* has ten vertices, and is typically drawn as a five sided star inside a pentagon, with corresponding vertices connected:



The vertices of the Petersen graph are the $$10=\binom{5}{2}$$ two elements subsets of a 5 element set, and two vertices are adjacent if the corresponding subsets are disjoint.


Types of graphs
===

Definition: Disjoint union
===

Given two graphs $$\Gamma_1$$ and $$\Gamma_2$$, the disjoint union $$\Gamma_1\sqcup \Gamma_2$$ is obtained by taking the disjoint union of both the vertices and edges of $$\Gamma_1$$ and $$\Gamma_2$$.  So $$\Gamma_1\sqcup\Gamma_2$$ consists of a copy of $$\Gamma_1$$ and a copy of $$\Gamma_2$$, with no edges in between the two graphs.

Definition: Connected and disconnected
===

A graph $$\Gamma$$ is *disconnected* if we can write $$\Gamma=\Gamma_1\sqcup \Gamma_2$$ for two proper subgraphs $$\Gamma_1$$ and $$\Gamma_2$$.

A graph $$\Gamma$$ is *connected* if it is not disconnected.

Definition: Bipartite
====

A graph $$\Gamma$$ is bipartite if we can color the vertices of $$\Gamma$$ red and blue, so that every edge of $$\Gamma$$ connects a red edge and a blue edge.


An important example of a bipartite graph is the *complete bipartite graph* $$K_{m+n}$$.  This graph consists of $$m+n$$ vertices, $$m$$ of them red and $$n$$ of them blue, and between every red and blue vertex there is exactly one edge.  $$K_{m,n}$$ has as many edges as possible while still being simple and bipartite.

Definition: The complemenet
====

The *complement* of a simple graph $$\Gamma$$, written $$\overline{\Gamma}$$ or $$\Gamma^c$$, has the same vertex set of $$\Gamma$$, but the ``opposite'' edge set: $$v_1,v_2\in V(\overline{\Gamma})$$ are adjacent in $$\overline{\Gamma}$$ if and only if they are *not* adjacent in $$\Gamma$$.

Quick exercises/examples to check:

1. The complement of the complement is the original graph: $$(\Gamma^c)^c=\Gamma$$
2. $$\overline{K}_n=E_n$$
3. $$\overline{K}_{m,n}=K_m\sqcup K_n$$


Degrees and the handshake lemma
---

Euler's handshaking lemma:
====
The sum of the degrees of the vertices of a graph is twice the number of edges of the graph:

$$\sum_{v\in V(\Gamma)}d(v)=2|E(\Gamma)|$$

Proof:
===

Each edge has two ends; each end contributes 1 to the degree of one vertex, and hence to the sum of all the degrees.  $$\square$$

