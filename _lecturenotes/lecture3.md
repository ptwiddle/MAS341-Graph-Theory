---
layout: lecture
title: Lecture 3&#58; Connectedness.  Walks, trails and paths.
comments: True
---

If the edges in a graph $$\Gamma$$ represent connections, it is obvious to ask whether $$\Gamma$$ as a whole is "connected".  There are two seemingly different ways of making this precise; today we introduce these and show that they are the same.

It may be easiest to define what it means for a graph $$\Gamma$$ to be *disconnected*.

Definition: Disjoint union
===

Given two graphs $$\Gamma_1$$ and $$\Gamma_2$$, the *disjoint union* $$\Gamma_1\sqcup \Gamma_2$$ is obtained by taking the disjoint union of both the vertices and edges of $$\Gamma_1$$ and $$\Gamma_2$$.  So $$\Gamma_1\sqcup\Gamma_2$$ consists of a copy of $$\Gamma_1$$ and a copy of $$\Gamma_2$$, with no edges in between the two graphs.

Definition: Disconnected
===

A graph $$\Gamma$$ is *disconnected* if we can write $$\Gamma=\Gamma_1\sqcup \Gamma_2$$ for two proper (i.e., not all of $$\Gamma$$) subgraphs $$\Gamma_1$$ and $$\Gamma_2$$.

It then makes sense to say that $$\Gamma$$ is *connected* if it is not disconnected.  However, the more intuitive notion of being connected is that "you can get from any vertex to any other", which we now make precise.


Walks, Trails, Paths
----

Definition
===
A *walk* in a graph $$\Gamma$$ is a sequence 

$$v_0, e_1, v_1,e_2, v_2,\dots, v_{n-1}, e_n, v_n$$

where 
 - the $$v_i$$ are vertices
 - the $$e_j$$ are edges
 - edge $$e_j$$ goes between vertices $$v_{j-1}$$ and $$v_j$$


Note that, when the graph $$\Gamma$$ does not have multiple edges, it is enough to record just the $$v_i$$, but if $$\Gamma$$ has multiple edges that just knowing the vertices does not determine the walk.



 We say that the walk is between vertices $$a$$ and $$b$$ if $$a=v_0$$ to vertex $$b=v_n$$.  Thus, it is natural to say that a graph $$\Gamma$$ is connected if there is a walk between any two vertices $$a,b\in\Gamma$$.  We now show that this agrees with our previous definition of connected.


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


Types of Walks
-------

Many questions in graph theory ask whether or not a walk of a certain type exists on a graph: we introduce some notation that will be needed for these questions.
 

We say a walk is *closed* if it starts and ends on the same vertex; i.e., $$v_0=v_n$$.  The *length* of a walk is $$n$$, the number of edges in it.  The *distance* between two vertices $$v$$ and $$w$$ is the length of the shortest walk from $$v$$ to $$w$$, if one exists, and $$\infty$$ if one does not exist.


Walks, trails and paths
======

 - If the edges $$e_i$$ of the walk are all distinct, we call it a *trail*
 - If the vertices $$v_i$$ of the walk are all distinct (except possibly $$v_0=v_m$$), we call the walk a *path*.  The exception is to allow for the possibility of closed paths.


Lemma
===

Let $$v,w\in V(\Gamma)$$.  The following are equivalent:

1. There is a walk from $$v$$ to $$w$$.
2. There is a trail from $$v$$ to $$w$$
3. There is a path from $$v$$ to $$w$$.

Proof
===

Obviously, 3 implies 2 which implies 1, as any path is a trail, and any trail is a walk.  

That 1 implies 3 is intuitively obvious: if you repeat a vertex, then you've visited someplace twice, and weren't taking the shortest route.  Let's make this argument mathematically precise.

Suppose we have a walk $$v=v_0,e_1,\dots, e_m, v_m=w$$ that is not a path.  Then, we must repeat some vertex, say $$v_i=v_k$$, with $$i<k$$.  Then we can cut out all the vertices and edges between $$v_i$$ and $$v_k$$ to obtain a new walk 

$$v=v_0,e_1, v_1,\dots, e_i, v_i, e_{k+1}, v_{k+1}, e_{k+2}, v_{k+2}, \dots, v_m$$.  

Since $$i<k$$, the new walk is strictly shorter than our original walk.  Since the length of a walk is finite, if we iterate this process the result must eventually terminate.  That means all our vertices are distinct, and hence is a path.  $$\square$$





