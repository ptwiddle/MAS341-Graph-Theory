---
layout: lectue
tite: Lectue 1&#; Examples, definitions, instant insanity
comments: True
---

Course Policies
====

We began with a brief discussion of course policies, which are available online here.  


Graphs
===

Graphs usually (but not always) are thought of showing how things are set of things are connected together.

Definition of a graph
---

A *graph* $$\Gamma$$ consists of 
 - a set $$V(\Gamma)$$ of vertices 
 - a set $$E(\Gamma)$$ of edges 
Each edge either connects two vertices of $$V(\Gamma)$$ together, or connects an edge to itself.


See the slides for many picture examples, but here are common examples:
 -  cities as vertices and roads connecting them as edges
 - people as vertices and an edge between two people if they know each other
 - atoms in a molecule with an edge between them if they are connected by a covalent bond
 - countries on a map as vertices, and edges shared border


A few more definitions
----

There are two features of graphs that are sometimes convenient to not allow.  A *loop* is an edge that connects a vertex to itself, and a *multiple edge* is when there is more than one edge connecting the same two vertices.  A graph without these features is called *simple*.  

The *degree* or *valency* of a vertex is the number of edges that connect to it; a graph is *regular* if every vertex has the same degree $$k$$.

Instant Insanity
====

We'll begin by giving a concrete application of graph theory to the puzzle ``instant insanity'', known sometimes as the four cubes problem.

In this puzzle, one is given four cubes.  Each face of each cube is painted one of four different colours: blue, green, red or yellow.  The goal is to line the four cubes up in a row, so that along the four long edges (front, top, back, bottom) each of the four colours appears eactly once.

Depending on how the cubes are coloured, this may be not be possible, or there may be many such possibilities.  In the original instant insanity, there is exactly one solution; in lecture, I walked through proving the following example has no solutions.  Given any set of four cubes, you should be able to either find a solution, or prove that no such solution exists.

Connection to graph theory
----



