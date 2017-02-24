---
layout: lecture
title: Lecture 2&#58; Instant Insanity, Isomorphisms
comments: True
---
[Slides from class](/MAS341-Graph-Theory/Slides/Lecture2.html).


Instant Insanity
---

A concrete, nontrivial application of graph theory is as a tool to solve the puzzle ``instant insanity'', known sometimes as the four cubes problem.

Basic setup
===

In this puzzle, one is given four cubes.  Each face of each cube is painted one of four different colours: blue, green, red or yellow.  The goal is to line the four cubes up in a row, so that along the four long edges (front, top, back, bottom) each of the four colours appears eactly once.

Depending on how the cubes are coloured, this may be not be possible, or there may be many such possibilities.  In the original instant insanity, there is exactly one solution.  I have made a <a href="https://www.youtube.com/watch?v=GsbhRfjaaN8">video</a> that explains how to use graph theory to show the solution to the original onstant insanity.

There are many variations on Instant Insanity, discussion of which can be found, for [here](http://www.cs.brandeis.edu/~storer/JimPuzzles/ZPAGES/zzzInstantInsanity.html) and [here](http://www.jaapsch.net/puzzles/insanity.htm).  There's also [a commercial](https://www.youtube.com/watch?v=CQ2gHSKZBEw) for the game. 


An impossible example
---

In lecture, I walked through proving that the following example has no solutions.  The work was done on the board and not in the slides, but I will present the work here.

The four cubes in question are:

<image src="../Slides/Pictures/ImpossibleCubes.png"></image>

Enter graph theory
===

We will now construct a graph that encodes the important part of the structure of the cubes. 

The vertices of the graph will be the four colors, B, G, R and Y.  We will put an edge between two colors each time they appear as opposite faces on a cube, and we will label that edge with a number 1-4 denoting which cube the two opposite faces appear.  So from the first cube, there will be a loop at B, and edge between G and R, and an edge between Y and R.

The graph corresponding to the four cubes above is the following:

<image src="../Slides/Pictures/InstantInsanityImpossibleGraph.JPG"></image>


Proving our cubes were impossible
===

How does this graph help us study the solutions of the Instanity Insanity puzzle?  Suppose we had an arrangement of the cubes that was a solution.  Then, from each cube, pick the edge representing the colors facing front and back on that cube.  These four edges are a subgraph of our original graph, with one edge of each label, since we picked one edge from each cube.  Furthermore, since we assumed the arrangement of cubes was a solution of instant insanity, each color appears once on the front face and once on the back.  In terms of our subgraph, this translates into asking that each vertex has degree two.  

We got another subgraph satisfying these two properties by looking at the faces on the top and bottom for each cube and taking the corresponding edges.  Furthermore, these two subgraphs do not have any edges in common.

Thus, given a solution to the instant insanity problem, we found a pair of subgraphs $$S_1, S_2$$ satisfying:

1. Each subgraph $$S_i$$ has one edge with each label 1,2,3,4
2. Every vertex of $$S_i$$ has degree 2
3. No edge of the original graph is used in both $$S_1$$ and $$S_2$$

As an exercise, one can check that given a pair of subgraphs satisfying 1-3, one can produce a solution to the instant insanity puzzle.

Thus, to show the set of cubes we are currently examining does not have a solution, we need to show that the graph does not have two subgraphs satisfying properties 1-3.

To do, this, we catalog all graphs satisfying properties 1-2.  If every vertex has degree 2, either 

1. Every vertex has a loop
2. There is one vertex with a loop, and the rest are in a triangle
3. There are two vertices with loops and a double edge between the other two vertices
4. There are two pairs of double edges
5. All the vertices live in one four cycle

A subgraphs of type 1 is not possible, because G and R do not have loops.

For subgraphs of type 2, the only triangle is G-R-Y, and B does have loops.  The edge between Y-G must be labeled 3, which means the loop at B must be labeled 1.  This means the edge between G and R must be labeled 4 and the edge between Y and R must be 2, giving the following subgraph:

<a href="http://www.presheaf.com/?d=d4oj3rb54s1o455d3y411052m3sm"><img src="http://presheaf.com/cache/d4oj3rb54s1o455d3y411052m3sm.png" title="click to go to presheaf.com for editing"/></a>

For type 3, the only option is to have loops at B and Y and a double edge between G and R.  We see the loop at Y must be labeled 2, one of the edges between G and R must be 4, and the loop at B and the other edge between G and R can switch between 1 and 3, giving two possibilities:

<a href="http://www.presheaf.com/?d=d4q2c25256yh02f391k2uwf95r4x"><img src="http://presheaf.com/cache/d4q2c25256yh02f391k2uwf95r4x.png" title="click to go to presheaf.com for editing"/></a>

and

<a href="http://www.presheaf.com/?d=d1x1h4f1nv494b64t68504rc12nd"><img src="http://presheaf.com/cache/d1x1h4f1nv494b64t68504rc12nd.png" title="click to go to presheaf.com for editing"/></a>


For subgraphs of type 4, the only option would be to have a double edge between B and G and another between Y and R; however, none of these edges are labeled 3 and this option is not possible.

Finally, subgraphs of type 5 cannot happen because B is only adjacent to G and to itself; to be in a four cycle it would have two be adjacent to two vertices that aren't itself.

This gives three different possibilities for the subgraphs $$S_i$$ that satisfy properties 1 and 2.  However, all three possibilities contain the the edge labeled 4 between G and R; hence we cannot choice two of them with disjoint edges, and the instant insanity puzzle with these cubes does not have a solution.




Isomorphisms: When are two graphs "the same"?
-----

It is possible to draw the same graph in the plane in many different ways -- e.g., the pentagon and the five sided star are two different ways of drawing $$C_5$$.  

If two graphs are "the same" in this way, we say they are *isomorphic*.

Definition
====

An *isomorphism* $$\varphi:G\to H$$ of simple graphs is a bijection $$\varphi:V(G)\to V(H)$$ that preserves the number of edges between vertices.  That is, if $$v,w\in V(G)$$, then the number of edges between $$v$$ and $$w$$ in $$G$$ is equal to the number of edges between $$\varphi(v)$$ and $$\varphi(w)$$ in $$H$$.


Example
====

This animated gif shows several graphs isomorphic to the Petersen graph, and demonstrates that they are isomorphic:

<image src="../Slides/Pictures/PetersenIsomorphismAnimated.gif"></image>

Graph isomorphism problem
---

The *graph isomorphism problem* is to decide whether or not two given graphs $$G, H$$ are isomorphic.  

General discussion for mathematical cultural literacy
===

The isomorphism problem is of fundamental importance to theoretical computer science. Apart from its practical applications, the exact difficulty of the problem is unknown.  Clearly, if the graphs are isomorphic, this fact can be easily demonstrated and checked, which means the Graph Isomorphism is in NP.  

Most problems in NP are known either to be easy (solvable in polynomial time, P), or at least as difficult as any other problem in NP (NP complete).  This is not true of the Graph Isomorphism problem.   In November of last year, Laszlo Babai announced a quasipolynomial-time algorithm for the graph isomorphism problem -- you can read about this work in [this great popular science article](https://www.quantamagazine.org/20151214-graph-isomorphism-algorithm/).

What you have to be able to do
====

Although solving the graph isomorphism problem for general graphs is quite difficult, doing it for small graphs by hand is not too bad and is something you must be able to do for the exam.

If the two graphs are actually isomorphic, you have to actually write down an explicit isomorphism $$\varphi:G\to H$$ should be given.  

 If they are not isomorphic, you have to prove that they are not isomorphic.  Usually this is done by giving an *obstruction* -- something that is different between the two graphs.  One easy example is that isomorphic graphs have to have the same number of edges and vertices.  

Another, only slightly more advanced invariant is the degree sequence of a graph that we saw last lecture in our discussion of chemistry.

If $$\varphi:G \to H$$ is an isomorphism of graphs, than we must have $$d(\varphi(v))=d(v)$$ for all vertices $$v$$, and so the degree sequence must be preserved.  However, just because two graphs have the same degree sequences does not mean they are isomorphic.

