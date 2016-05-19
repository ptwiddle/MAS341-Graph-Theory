---
layout: lecture
title: Lecture 2&#58; Examples, isomorphisms, degrees
comments: True
---
[Slides from class](/MAS341-Graph-Theory/Slides/Lecture2.html).


Examples and types of graphs
---

A few basic examples
===

1. The *complete graph* $$K_n$$ has $$n$$ vertices, and each vertex is connected to every other vertex by exactly one edge (so $$K_n$$ is a simple graph)
2. The *empty graph* $$E_n$$ has $$n$$ vertices and no edges between them
3. The *path* $$P_n$$ consists of $$n$$ vertices, $$v_1,\dots, v_n$$, and $$n-1$$ edges, $$e_1,\dots, e_{n-1}$$, where $$e_i$$ connects $$v_i$$ with $$v_{i+1}$$
4. The *cycle graph* $$C_n$$ is obtained from the path $$P_n$$ by adding one edge, between $$v_n$$ and $$v_1$$
5. The *wheel* $$W_{n+1}$$ is obtained from the cycle $$C_n$$ by adding one more vertex $$v_0$$, and connecting to every edge in $$C_n$$
6. The *Petersen graph* has ten vertices, and is typically drawn as a five sided star inside a pentagon, with corresponding vertices connected:



Note that in the notation we ahve chosen above, for a graph $$G_n$$, $$n$$ is the number of vertices.

Question:
====
How many edges are in $$K_n, P_n, C_n, W_n$$?


When are two graphs "the same"?
-----

It is possible to draw the same graph in the plane in many different ways -- e.g., the pentagon and the five sided star are two different ways of drawing $$C_5$$.  

If two graphs are "the same" in this way, we say they are *isomorphic*.

Definition
====

An *isomorphism* $$\varphi:G\to H$$ is a bijection $$\varphi:V(G)\to V(H)$$ that preserves the number of edges between vertices.  That is, if $$v,w\in V(G)$$, then the number of edges between $$v$$ and $$w$$ in $$G$$ is equal to the number of edges between $$\varphi(v)$$ and $$\varphi(w)$$ in $$H$$.


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

Another, only slightly more advanced invariant is the *degree sequence* of a graph.

Definition: degree sequence
====
The *degree sequence* of a graph is just the list (with multiplicity) of the degrees of all the vertices.



Degrees and the handshake lemma
---

Euler's handshaking lemma:
====
The sum of the degrees of the vertices of a graph is twice the number of edges of the graph:

$$\sum_{v\in V(\Gamma)}d(v)=2|E(\Gamma)|$$

Proof:
===
Each edge has two ends; each end contributes 1 to the degree of one vertex, and hence to the sum of all the degrees.  $$\square$$

Graph theory in Chemistry
----

In organic chemistry, atoms are joined together by covalent bonds; we represent this in a graph with the atoms as vertices and the edges representing the bonds.  The location of the element on the periodic table determines the valency of the vertices corresponding to that element:

 
- Hydrogen (H) and Fluorine (F) have degree 1
- Oxygen (O) and Sulfur (S) have degree 2 
- Nitrogen (N) and Phosphorous (P) have degree 3 
- Carbon (C) has degree 4 

Usually, most of the atoms involved are carbon and hydrogen.  Carbon atoms are not labelled with a C, but just left blank, while hydrogen atoms are left off completely.  One can then complete the full structure of the molecule using the valency of each vertex.