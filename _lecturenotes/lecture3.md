---
layout: lecture
title: Lecture 3&#58; Walks, paths, cycles
comments: True
---

Types of graphs
---

Definition: Disjoint union
===

Given two graphs $$\Gamma_1$$ and $$\Gamma_2$$, the disjoint union $$\Gamma_1\sqcup \Gamma_2$$ is obtained by taking the disjoint union of both the vertices and edges of $$\Gamma_1$$ and $$\Gamma_2$$.  So $$\Gamma_1\sqcup\Gamma_2$$ consists of a copy of $$\Gamma_1$$ and a copy of $$\Gamma_2$$, with no edges in between the two graphs.

Definition: Connected and disconnected
===

A graph $$\Gamma$$ is *disconnected* if we can write $$\Gamma=\Gamma_1\sqcup \Gamma_2$$ for two proper (i.e., not all of $$\Gamma$$) subgraphs $$\Gamma_1$$ and $$\Gamma_2$$.

A graph $$\Gamma$$ is *connected* if it is not disconnected.

Definition: Bipartite
====

A graph $$\Gamma$$ is bipartite if we can color the vertices of $$\Gamma$$ red and blue, so that every edge of $$\Gamma$$ connects a red vertex and a blue vertex.


An important example of a bipartite graph is the *complete bipartite graph* $$K_{m,n}$$.  This graph consists of $$m+n$$ vertices, $$m$$ of them red and $$n$$ of them blue, and between every red and blue vertex there is exactly one edge.  $$K_{m,n}$$ has as many edges as possible while still being simple and bipartite.

Definition: The complement
====

The *complement* of a simple graph $$\Gamma$$, written $$\overline{\Gamma}$$ or $$\Gamma^c$$, has the same vertex set of $$\Gamma$$, but the ``opposite'' edge set: $$v_1,v_2\in V(\overline{\Gamma})$$ are adjacent in $$\overline{\Gamma}$$ if and only if they are *not* adjacent in $$\Gamma$$.

Quick exercises/examples to check:

1. The complement of the complement is the original graph: $$(\Gamma^c)^c=\Gamma$$
2. Complement of the complete graph is the empty graph: $$\overline{K}_n=E_n$$
3. Complement of the complete bipartite graph is the disjoint union of two complete graphs: $$\overline{K}_{m,n}=K_m\sqcup K_n$$

Walks, Trails, Paths
----

Definition
===
 - A *walk* in a graph $$\Gamma$$ is a sequence of edges $$e_1,\dots, e_m$$ so that each pair of consecutive edges $$e_i, e_{i+1}$$ share a vertex; that is, there are vertices $$v_0,\dots, v_m$$ so that edge $$e_i$$ goes between $$v_{i-1}$$ and $$v_i$$.  The number of edges $$m$$ is called the *length* of the walk.

Note that, when the graph $$\Gamma$$ does not have multiple edges, it is enough to record just the vertices.

We say a walk is *closed* if it starts and ends on the same vertex; i.e., $$v_0=v_m$$.

 - If the edges $$e_i$$ of the walk are all distinct, we call it a *trail*
 - If the vertices $$v_i$$ of the walk are all distinct (except possibly $$v_0=v_m$$), we call the walk a *path*.  The exception is to allow for the possibility of closed paths.

The *distance* between two vertices $$v$$ and $$w$$ is the length of the shortest walk from $$v$$ to $$w$$, if one exists, and $$\infty$$ if one does not exist.

Lemma
===

Let $$v,w\in V(\Gamma)$$.  The following are equivalent:

1. There is a walk from $$v$$ to $$w$$.
2. There is a trail from $$v$$ to $$w$$
3. There is a path from $$v$$ to $$w$$.

Proof
===

Obviously, 3 implies 2 which implies 1, as any path is a trail, and any trail is a walk.  

To see that 1 implies 3, suppose we have a walk $$v=v_0,\dots, v_m=w$$ that is not a path; say, $$v_i=v_k$$, with $$i<k$$.  Then we can cut out all the vertices between $$v_i$$ and $$v_k$$ to obtain a new walk $$v=v_0,v_1,\dots, v_i, v_{k+1}, v_{k+2}, \dots, v_m$$.  

Since $$i<k$$, the new walk is strictly shorter.  Since the length of a walk is finite, if we continue this process we'll eventually get a path $$\square$$


Next time, we will prove the following two lemmas:


Lemma
===

The following are equivalent:

1. $$\Gamma$$ is connected.
2. There is a walk between any two vertices $$v, w\in V(\Gamma)$$


Lemma
===
A graph is bipartite if and only if it does not have an odd cycle.




