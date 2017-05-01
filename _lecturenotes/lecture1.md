---
layout: lecture
title: Lecture 1&#58; Introduction, Euler's Handshaking Lemma
comments: True
---
[Slides from class](/MAS341-Graph-Theory/Slides/Lecture1.html).


Course Policies
---

We began with a brief discussion of course policies, which are available online <a href="/MAS341-Graph-Theory/Policies/">here</a>.  


Graphs
---

Graphs usually (but not always) are thought of showing how things are set of things are connected together.

Definition of a graph
===

A *graph* \\(\Gamma\\) consists of: 

- a set \\(V(\Gamma)\\) of vertices 
- a set \\(E(\Gamma)\\) of edges 

Each edge either connects two vertices of \\(V(\Gamma)\\) together, or connects a vertex to itself.

Examples
===

See the slides for many picture examples, but here are some common examples:

-  cities as vertices and roads connecting them as edges
- people as vertices and an edge between two people if they know each other
- atoms in a molecule as vertices, with an edge between them if they are connected by a covalent bond
- countries on a map as vertices, and shared borders as edges


A few more definitions
===

There are two features of graphs that are sometimes convenient to not allow.  

A *loop* is an edge that connects a vertex to itself, and a *multiple edge* is when there is more than one edge connecting the same two vertices.  A graph without these features is called *simple*.  

We say two vertices are *adjacent* if there is an edge between them.

The *degree* or *valency* of a vertex in a simple graph is the number of vertices it is adjacent to.

A first question
----

Suppose you are at a party with six other people, so that there are seven people total at the party.  Is it possible that everybody knows exactly three other people at the party?

To translate this into graph theory, we make the people vertices, and put an edge between two people if they know each other.  We are then asking if a graph exists with seven vertices, where each vertex has degree three.

It turns out that this is not possible; one way to prove this would be doing a case by case analysis of trying to make such a graph, but such proofs are usually long, messy, and not particularly enlightening.  

Instead, we argued as follows: suppose that everyone at the party shook hands with the people they knew, but not with the people they don't know.  How many handshakes would occur?

It is immediate from the definition that the number of handshakes would be the number of edges in the graph.  But we could also count the number of handshakes in another way: each person is going to shake hands three times, so people will be involved in handshakes 3*7=21 times.  But since each handshake involves two people, this should be twice the number of handshakes.  From this reasoning, we see there should be 21/2=10.5 edges in the graph, which is absurd, and so we see that such a party is not possible.

The argument given above easily generalizes to give

Euler's handshaking lemma:
====
The sum of the degrees of the vertices of a graph is twice the number of edges of the graph:

\\[\sum_{v\in V(\Gamma)}d(v)=2|E(\Gamma)|\\]

Proof:
===
Each edge has two ends; each end contributes 1 to the degree of one vertex, and hence to the sum of all the degrees.  \\(\square\\)

Graph theory in Chemistry
----

In organic chemistry, atoms are joined together by covalent bonds; we represent this in a graph with the atoms as vertices and the edges representing the bonds.  The location of the element on the periodic table determines the valency of the vertices corresponding to that element:
 
- Hydrogen (H) and Fluorine (F) have degree 1
- Oxygen (O) and Sulfur (S) have degree 2 
- Nitrogen (N) and Phosphorous (P) have degree 3 
- Carbon (C) has degree 4 

Usually, most of the atoms involved are carbon and hydrogen.  Carbon atoms are not labelled with a C, but just left blank, while hydrogen atoms are left off completely.  One can then complete the full structure of the molecule using the valency of each vertex.

Graphs coming from organic chemistry do not have to be simple -- sometimes there are double bonds, where a pair of carbon atoms have two edges between them.

Definition: degree sequence
====
The *degree sequence* of a graph is just the list (with multiplicity) of the degrees of all the vertices.  

So, knowing the chemical composition of a molecule determines the degree sequence of its corresponding graph.  However, it is possible that the same set of atoms may be put together into a molecule in more than one different ways.  In terms of graphs, this corresponds to "different" graphs that have the same degree sequence.