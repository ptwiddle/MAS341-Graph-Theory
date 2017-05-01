---
layout: lecture
title: Lecture 20&#58; Catch-up, 5-Colour Theorem
comments: True
---


Five Colour Theorem
----

Our goal today is to prove that any planar graph can be coloured with 5 colours; as a warm-up we prove that it can be coloured with 6 colours; the proof for 5 will be a refinement of this proof.


Theorem
====
Any planar graph has $$\chi(G)\leq 6$$.

Proof
===

The proof of this theorem is in some ways very similar to the previous proof.  We will induction, deleting vertices one by one.  

We need to use that $$G$$ is planar somehow.  And from the previous theorem, we see that we want $$G$$ to have vertices with low degree, because deleting them leads to efficient colourings.  The following lemma connects these ideas

Lemma
====

Any planar graph $$G$$ has a vertex $$v$$ of degree at most $$5$$.  

Before proving this lemma, we will see how the lemma leads to a proof of the 6 colour theorem.

We again use induction.  As a base case, it is clear than any planar graph with at most 6 vertices can be coloured with 6 colours.  Now, suppose that all planar graphs with less than $$k$$ vertices can be coloured with 6 colours, and suppose $$\Gamma$$ is a planar graph with $$k$$ vertices.  We must show that $$\chi(\Gamma)\leq 6$$.

By the Lemma, since $$\Gamma$$ is planar it has a vertex $$v$$ with $$d(v)\leq 5$$.  Deleting $$v$$, the graph $$\Gamma\setminus v$$ has strictly less than $$k$$ vertices, and hence can be coloured with 6 colours.  Now, taking this colouring and trying to extend it to a colouring of $$\Gamma$$ we just have to colour $$v$$.  But $$v$$ is only adjacent to 5 vertices, and so at least one of our six colours is not used in these vertices.  If we colour $$v$$ one of these unused colours, then we have the colouring we want.  


We now prove the lemma:

Proof of Lemma
====
The proof uses Euler's theorem and handshaking.  Suppose that $$G$$ has $$v$$ vertices and $$e$$ edges, and we have drawn $$G$$ on the plane with $$f$$ faces.  Then by Euler's theorem $$v-e+f=2$$.  

Now, suppose that every vertex had degree at least 6.  Then by the handshaking lemma, we see that $$6v\leq 2e$$, or $$v\leq e/3$$  On the other hand, if we want to colour $$G$$ it can't have any loops, and multiple edges don't effect vertex colourings, and so we may assume $$G$$ simple.  This means that every face has at least 3 vertices, and so $$3f\leq 2e$$, or $$f\leq 2/3 e$$.  

Thus, we have

$$\chi(G)=v-e+f\leq e/3-e+2/3 e=0$$

a contradiction, and so we our initial assumption that every vertex of $$G$$ has degree at least 6 must have been wrong.  $$\square$$



Having proven the 6 colour theorem, we modify the proof to prove the 5 colour theorem.


Theorem
====

Any planar graph $$G$$ can be coloured with at most five colours.

Proof
===

We begin by following closely the proof of the six colour theorem.  We will again use induction on the number of vertices; clearly any graph with at most five vertices can be coloured with at least five colours, so we have a base case.

Now assume that every planar graph with at most $$k$$ vertices can be coloured with five colours, and suppose that $$G$$ is a planar graph with $$k+1$$ vertices.

In the proof of the 6 colour theorem, we proved that $$G$$ has a vertex $$v$$ of degree at most 5.  As in the proof of the six colour theorem, we delete that vertex $$v$$; the resulting graph $$G\setminus v$$ has $$k$$ vertices and hence can be 5 coloured, we thus colour all the vertices of $$G$$ besides $$v$$ with these 5 colours.  

If $$v$$ is adjacent to less than five vertices, or if the 5 vertices $$G$$ is adjacent to use less than 5 colours, then this colouring can be extended toa c olouring of all $$G$$ and we are done.  

Thus, let let $$w_1, w_2, w_3, w_4, w_5$$ be the 5 vertices adjancent to $$v$$, written in cyclic order, and suppose that $$w_i$$ is coloured $$i$$.

We can't extend the colouring of $$G\setminus v$$ to $$v$$ as it currently stands, so will change the colouring of $$G\setminus v$$ slightly, by switching some subset of pairs of colours.

As a warm-up, note that we can pick any two colours, and switch all the vertices labelled in those colours, and we'll still have a leagl colouring.  (You can just think of this as changing the name of the two colours).

More generally, consider the induced subgraph $$H_{1,3}$$ of $$G\setminus v$$ consisting of only those vertices that are coloured 1 or 3.  The subgraph $$H_{1,3}$$ may consist of multiple components.  We can just switch the colours of the 1s and 3s of a single component, and it will still be a legal colouring.

Thus, if $$w_1$$ and $$w_3$$ are in different components of $$H_{1,3}$$, we can switch the colours of all the vertices in the component that $$w_3$$ is in, then $$w_1$$ and $$w_3$$ are both coloured 1, and we may extend the colouring by $$v$$ by making it 1.

So, we need only consider the case that $$w_1$$ and $$w_3$$ are in the same component of $$H_{1,3}$$.  This means that there is a path from $$w_1$$ to $$w_3$$ in $$H_{1,3}$$; that is, a path $$P=w_1-u_1-u_2\cdots-u_k=w_3$$ consisting of vertices $$u_i$$ coloured only 1 and 3.


of vertices between $$w_1$$ and $$w_3$$ in $$G\setminus v$$ consisting only of vertices coloured 1 and 3.

Now, we try to play the same game with $$w_2$$ and $$w_4$$, and consider the subgraph $$H_{2,4}$$ consisting of only those vertices coloured 2 and 4.  If $$w_2$$ and $$w_4$$ lie on different components of $$H_{2,4}$$, we can switch the colours on the component of $$H_{2,4}$$ containing $$w_4$$, which will make $$w_4$$ coloured 2, and we can colour $$v$$ with colour 4.

Thus, we need to consider the case where $$w_2$$ and $$w_4$$ are on the same component of $$H_{2,4}$$, thus, there is chain $$P^\prime=w_2-y_1-y_2\cdots-y_k=w_4$$ consisting only of vertices coloured 2 and 4.

Thus we have two walks $$P$$ and $$P^\prime$$ in the plane, that cannot share and vertices, a contradiction, as they'd have to cross over each other.  $$\square$$