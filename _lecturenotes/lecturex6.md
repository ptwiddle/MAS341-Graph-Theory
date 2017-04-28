---
layout: lecture
title: Lecture 16&#58; Euler's Theorem and applications
comments: True
---


We ended this morning's lecture by introducing the concept of the face of a graph, and of the dual graph.  In this lecture we prove Euler's theorem, which gives a relation between the number of edges, vertices and faces of a graph.


We begin by counting the number of vertices, edges, and faces of some graphs on surfaces -- the tetrahedron (or triangular pyramid) has 4 vertices, 6 edges, and 4 faces; the cube has 6 vertices, 12 edges, and 8 faces, etc.

Euler's Theorem
======

Let \\(\Gamma\\) be a graph drawn on the sphere, and suppose that $$\Gamma$$ has $$v$$ vertices, $$e$$ edges, and $$f$$ faces.  Then $$v-e+f=2$$.

Proof idea 1: 
=====

One way to prove it is the following: if we delete an edge from $$\Gamma$$, we will (usually) merge two faces into one, and thus have one less edge and one less face; this does not change $$v-e+f$$.

Similarly, if we have a vertex of degree 2, we can delete it and merge the two edges into one, getting one less edge and one less vertex, which does not change $$v-e+f$$.

By iteratively doing this two moves, you can get to a very basic graph or two, which you can check have $$v-e+f=2.  \square$$

Proof 2: Dual spanning trees
======
First, take a spanning tree $$T$$ of $$\Gamma$$; it has $$v$$ vertices, and since it is a tree it must have $$v-1$$ edges.

Now, we construct another graph $$\tau$$ as follows.  The vertices of $$\tau$$ will be the faces of our original graph $$\Gamma$$.  We will connect two vertices of $$\tau$$ if and only if they are connected by an edge *not* in our spanning tree $$T$$.  Thus, we see that $$\tau$$ is a subgraph of the dual graph of $$\Gamma$$, that contains all the vertices and every edge that isn't in $$T$$.

We first note that Euler's formula follows if we can show that $$\tau$$ is a tree as well, as then $$\tau$$ would have $$f$$ vertices and hence $$f-1$$ edges.  But since every edge of $$\Gamma$$ is either in $$T$$ or $$\tau$$ we have

$$v-e+f=|V(T)|-|E(T)|-|E(\tau)|+|V(\tau)|=1+1=2$$

To prove that $$\tau$$ is indeed a tree, we need to show $$\tau$$ is connected and has no cycles.  If $$\tau$$ were disconnected, then we claim $$T$$ would have a cycle.  Let $$\tau_1\subset \tau$$ be one of the connected components, and consider the union of all the faces in $$\tau_1$$.  This is some region of the sphere that isn't the whole thing; its boundary will be a union of circles.  But the boundary is also a union of edges in $$T$$; therefore, $$T$$ must contain a cycle, a contradiction.

We also need to show that $$\tau$$ has no cycles; this is just the "dual" of the above argument:  But if $$\tau$$ had a cycle, it would cut the sphere into two pieces, each of which would contain a vertex of $$T$$, and hence $$T$$ would be disconnected, a contradiction.  $$\square$$



Applications of Euler characteristic
------

Euler's theorem can be very useful in proving results about graphs on the sphere.  It's a bit awkward to use by itself -- it contains three variables, $$v, e$$ and $$f$$, so it is most useful when we already know some relations between these variables.  This may be best illustrated by our motivating example:


Theorem
====

It is impossible to draw a sphere with a videogame graph.

Proof
====

Recall that in a videogame graph, every vertex had degree 4, and each face was a square.

Suppose that we had such a graph drawn on the sphere; Euler's theorem gives us $$v-e+f=2$$; we need to use our other knowledge about the graph to get a contradiction.

How can we use that every vertex has degree 4?  The handshaking lemma!  Since every vertex has degree 4, the sum of the degrees of the vertices is just $$4v$$.  So the Handshaking Lemma just says $$4v=2e$$, and hence $$e=2v$$.

How can we use that every face has four sides?  We can do something just like the handshaking lemma, and count the number of times a face meets an edge.  On the one hand, each edge meets two faces, and so there are $$2e$$ places that an edge meets a face.  On the other hand, each face meets four edges, and so we see there are $$4f$$ times a face meets an edge, and so we have that $$2e=4f$$, or $$e=2f$$.

Putting $$e=2v$$ and $$e=2f$$ together, we see that $$f=v$$, and so $$v-e+f=v-2v+v=0$$, which is a direct contradiction of Euler's Formula $$,\quad \square$$


It's worth noting that "handshaking between edges and faces" actually *is* the handshaking lemma for the dual graph.

To generalize this, we note that we have three sources of relationships between $$v, e$$ and $$f$$ for a planar graph:

1. Euler's Formula
2. Handshaking between vertices and edges
3. Handshaking between edges and faces

These three relations can work together to prove a lot.  We give one more example now -- another proof that $$K_5$$ and $$K_{3,3}$$ aren't planar.  Yet another example can be found on the last homework set -- figuring out how many pentagons a football has.


Application: $$K_5$$ and $$K_{3,3}$$ aren't planar
=====

Let's try to give another proof that $$K_5$$ and $$K_{3,3}$$ aren't planar using Euler's formula.

First, let's show $$K_5$$ isn't planar.  We know explicitly that $$K_5$$ has 5 vertices and 10 edges, so if it were drawn on the sphere we would have

$$2=v-e+f=5-10+f=f-5$$

and so it would have to have 7 faces.  To get a contradiction, we need another way to get information about how many faces the drawing would have, which we can do via handshaking.  $$K_5$$ has no multiple edges or loops, and so the smallest number of edges a face could have is 3.  Thus, handshaking gives us

$$2e=\sum_{f \text{ face} } d(f)\geq \sum_f 3=3f$$
i.e., $$2e\geq 3f$$.  But we know $$e=10$$ and $$f=7$$, so we have a contradiction.

The argument for $$K_{3,3}$$ is similar; we know it has 6 vertices and 9 edges, so if it were drawn on the plane it would need to have 5 faces.  $$K_{3,3}$$ is simple, so again we have that each face has at least three sides, but this isn't strong enough for our purposes.  But, since $$K_{3,3}$$ is bipartite, it can't have any cycles of length three (or any odd number for that matter).  Thus, every face of any drawing of $$K_{3,3}$$ must have at least 4 sides.  Handshaking between faces and edges then gives $$2e\geq 4f$$, but there are 9 edges and 5 faces, a contradiction.  $$\square$$




Generalization: Euler characteristic and the beginnings of topology
-------

This is more just general mathematical culture than something you would see on the exam.

We have seen for that graphs drawn on the sphere, we have $$v-e+f=2$$.  Given that we've discussed drawing graphs on other surfaces, it becomes a natural question to ask if there's a similar relation for $$v-e+f$$ if we have a graph $$\Gamma$$ drawn on a different surface $$S$$.  You have to be a little bit more careful in defining what a face is: since the Jordan Curve Theorem fails for surfaces that aren't the sphere, it is not the case that every component of $$S\setminus \Gamma$$ will be a disk.

However, if we require that $$S$$ is drawn on the surface in such a way so that every "face" is actually a disk, then it turns out that $$v-e+f=\chi(S)$$, where $$\chi(S)$$ is some number, called the *Euler characteristic*, that depends *only* on the surface $$S$$, and not on the graph.

As an example, we saw that video game graphs always had $$v-e+f=0$$, and the natural way we got to make video game graphs were all living on the torus; the torus has euler characteristic 0.
