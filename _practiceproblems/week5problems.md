---
layout: problemsheet
title: Week 5 practice problems
comments: True
---

Spanning trees of $$K_{m,n}$$
-----

A *bipartite graph* has two types of vertices (say, red and blue), and only has edges between red vertices and blue vertices (never an edge from a red vertex to another red vertex, or a blue vertex to another blue vertex).

The *complete bipartite graph* $$K_{m,n}$$ has $$m$$ red vertices, $$n$$ blue vertices, and as many edges as possible while still being a simple graph -- namely, any red vertex $$v$$ is connected to every blue vertex $$w$$ by exactly one edge, so it has $$mn$$ edges.

Basics:
=====

Prove the following:

- $$K_{2,2}$$ has 4 spanning trees
- $$K_{2,3}$$ has 12 spanning trees
- $$K_{2,4}$$ has 32 spanning trees
- $$K_{3,3}$$ has 81 spanning trees

Challenge:
=======

It turns out that in general, $$K_{m,n}$$ has $$m^{n-1} n^{m-1}$$ spanning trees.  Can you prove this by adapting the Prüfer code?

Kruskal's algorithm
-------------------

A simple proof
=======

Suppose that the graph $$K_n$$ has the vertices labelled 1 through n, and the edge connecting vertex i and vertex j has weight i+j.  Prove that in the cheapest spanning tree, 1 has degree n-1, and so is connected directly to every other vertex.

A simple construction
=====

Suppose that $$1\leq m< n$$.  Describe a weighting the edges of $$K_n$$ so that it has exactly $$m$$ spanning trees of minimal weight.


Traveling Salesman
-----------------

A simple proof
======

Suppose that the graph $$K_n$$ has the vertices labelled 1 through n, and the edge connecting vertex i and vertex j has weight i+j.  Prove that the optimal solution to the TSP has cost n(n+1).  (Hint: Any solution to the TSP has weight n(n+1)).


A simple construction
======

The algorithm we gave for finding a lower bound for TSP depended on choosing a vertex.  Construct an example to show that the bound obtained can depend on which vertex we chose.