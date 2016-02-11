Junk - remove to make it post
---
layout: lecture
title: Lecture 3&#58; Walks, paths, cycles
comments: True
---
[Slides from class](/MAS341-Graph-Theory/Slides/Lecture3.html).


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

Definition: The complement
====

The *complement* of a simple graph $$\Gamma$$, written $$\overline{\Gamma}$$ or $$\Gamma^c$$, has the same vertex set of $$\Gamma$$, but the ``opposite'' edge set: $$v_1,v_2\in V(\overline{\Gamma})$$ are adjacent in $$\overline{\Gamma}$$ if and only if they are *not* adjacent in $$\Gamma$$.

Quick exercises/examples to check:

1. The complement of the complement is the original graph: $$(\Gamma^c)^c=\Gamma$$
2. $$\overline{K}_n=E_n$$
3. $$\overline{K}_{m,n}=K_m\sqcup K_n$$
