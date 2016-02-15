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

Lemma
===

The following are equivalent:

1. $$\Gamma$$ is connected.
2. There is a walk between any two vertices $$v, w\in V(\Gamma)$$

Proof
===

1 implies 2: Supppose that $$\Gamma$$ is connected, and let $$v, w\in V(\Gamma)$$; we want to show that there is a walk from $$v$$ to $$w$$. 

Define $$S\subset V(\Gamma)$$ to be the set of all vertices $$u\in V(\Gamma)$$ so that there is a walk from $$v$$ to $$u$$; we want to show that $$w\in S$$.

First, observe that there are no edges from $$S$$ to $$V(\Gamma)\setminus S$$.  Suppose that $$e$$ was an edge between $$a\in S$$ and $$b\in\Gamma\setminus S$$.  Since $$a\in S$$, by the definition of $$S$$ there is a walk $$v=v_0v_1v_2\cdots v_m=a$$ from $$v$$ to $$a$$.  We can add the edge $$e$$ to the end of the walk, to get a walk from $$v$$ to $$b$$, and hence by definition $$b\in S$$.  

Now suppose that $$w\notin S$$.  Then $$S$$ and $$V(\Gamma)\setminus S$$ are both nonempty, and by the above there are no edges between them, and so $$\Gamma$$ is not connected, a contradiction.

To prove 2 implies 1, we prove the contrapositive.  If $$\Gamma$$ is not connected, then there are two vertices $$v,w\in V(\Gamma)$$ so that there is no walk from $$v$$ to $$w$$. 

Suppose that $$\Gamma=\Gamma_1\sqcup\Gamma_2$$, and pick $$v\in V(\Gamma_1), w\in V(\Gamma_2)$$.  Any walk from $$v$$ to $$w$$ starts in $$V(\Gamma_1)$$ and ends in $$V(\Gamma_2)$$, and so at some point there must be an edge from a vertex in $$\Gamma_1$$ to a vertex in $$\Gamma_2$$, but there are no such edges $$\square$$

Lemma
===
A graph $$\Gamma$$ has a closed odd length path if and only if it has a closed walk of odd length.

Proof
====

A closed path of odd length is obviously a closed walk of odd length, so one implication is trivial.

Now, suppose $$v_0v_1\dots v_m=v_0$$ is a closed walk of odd length, but not a path.  Then some vertex is repeated; say, $$v_i=v_k$$, with $$i<k$$.  Then we may "pinch" the original closed walk into two smaller closed walks: $$v_0v_1\dots v_i v_{k+1}\dots v_m=v_0$$ and $$v_iv_{i+1}\dots v_k=v_{i+k}$$.  If these walks of lengths $$\ell_1$$ and $$\ell_2$$, then $$\ell_1+\ell_2=m$$, and since $$m$$ is odd one of the $$\ell_i$$ has to be odd, and we have have fund an odd walk of strictly shorter length.  Continuing this, we must eventually find an odd length walk with no vertices repeated.  $$\square$$


Lemma
===
A graph is bipartite if and only if it does not have an odd cycle.




Proof
===

Since the odd cycle is not bipartite, any graph containing an odd cycle cannot be partite; the harder direction is to show that if $$\Gamma$$ does not have an odd cycle, then it is bipartite.  

The proof proceeds by trying to color the vertices of $$\Gamma$$.  Pick any vertex $$v$$, and define $$S_k$$ to be the set of all vertices with distance exactly $$k$$ from $$v$$.  We will try to color $$\Gamma$$ by coloring the vertices in $$S_n$$ to be red if $$n$$ is even, and blue if $$n$$ is odd.  

Suppose that this is not a valid coloring; then we have a vertex $$a\in S_k$$ with $$k$$ even, adjacent to a vertex $$b\in S_\ell$$ with $$\ell$$ odd.

Since $$a\in S_k$$, there is a path $$v=v_0v_1\cdots v_k=a$$; and similarly since $$b\in S_\ell$$ there is a path $$v=w_0w_1\cdots w_\ell=b$$.  Concatening these gives us a closed walk $$a=v_kv_{k-1}\cdots v_0 w_1 w_2\cdots w_\ell=b$$ of length $$a+b$$ which is odd; since $$a$$ and $$b$$ are adjacent this gives us an odd walk in $$\Gamma$$, and hence by the previous lemma an odd path $$\square$$.

