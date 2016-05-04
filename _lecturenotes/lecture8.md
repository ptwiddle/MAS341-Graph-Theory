---
layout: lecture
title: Lecture 8&#58; More trees.  Chemistry and spanning trees
comments: True
---

Application: Alkanes
----

In organic chemistry, an *alkane* is a molecule with formula $$C_nH_{2n+2}$$.  The simplest Alkanes are methane $$CH_4$$, ethane $$C_2H_6$$ and propane $$C_3H_8$$.

![Alkanes](../Slides/Pictures/Hydrocarbons.jpg)

It appears from the graph that Alkanes are all trees; we prove that now.

Lemma
===
Any alkane $$C_nH_{2n+2}$$ is a tree.

Proof
===

In the last lecture, one characterization of trees we gave is that they were connected graphs on $$m$$ vertices with $$m-1$$ edges.  

Any graph of a molecule is necessarily connected, and so to prove an Alkane is a tree we must count the number of vertices and edges.  

There are $$n+(2n+2)=3n+2$$ vertices.  

We count the edges using the Handshaking lemma. Carbon atoms have valency 4, and there are $$n$$ of them, while Hydrogen atoms have valency 1.  Thus, the sum of all the degrees of the vertices is $$6n+2$$.  The number of edges is half of these, namely $$3n+1$$, which is 1 less than the number of vertices.  Since to be an atom it must be connected, we see that any Alkane is a tree.  $$\square$$


Isomers
----

Definition
===

Two molecules are *isomers* if they have the same molecular formula, but the molecules are put together in a different way.


When there are 1, 2 or 3 carbon molecules, the only possible Alkanes is a line of carbon molecules.  The resulting chemicals are methane, ethane, and propane.  when $$n=4$$, there are two possible alignments of the Carbon atoms: in a line, which is butane, or in a `T' shape, which is isobutane; when $$n=5$$, there are three different possibilities.  

Around 1875, Hamilton used graph theory to count the number of isomers of the Alkane $$C_nH_{2n+2}$$.  One can forget about the placement of the hydrogen molecules, and just count the struture of the carbon molecules; these two will be a tree.  Since the valency of Carbon is four the maximum degree of a vertex in these trees will be 4, and so counting isomers of $$C_nH_{2n+2}$$ is equivalent to counting isomorphism classes of trees with $$n$$ vertices, all of degree at most 4.



Spanning trees
----

Definition
===
Let $$\Gamma$$ be a graph.  A *spanning tree* of $$\Gamma$$ is a subgraph $$T\subset \Gamma$$ such that $$T$$ is a tree and $$T$$ contains every vertex of $$\Gamma$$.

Spanning trees are useful because they are a minimal connected subgraph that lets us get to all of $$\Gamma$$.  For instance, if the vertices are cities and the edges are roads, a spanning tree is a minimal set of edges that guarantee that you can get from any one city to another.

Examples:
===

The cycle graph $$C_n$$ has $$n$$ spanning trees obtained by deleting any one edge.  

Lemma:  
====
Every connected graph $$\Gamma$$ has a spanning tree.


Proof
====
By our characterisation of trees, if $$T$$ is connected and has no cycles, then $$T$$ is a tree.  So it is enough to find a connected subgraph $$T$$ of $$\Gamma$$ that contains every vertex.

Let $$H$$ be any subgraph of $$\Gamma$$ that is connected and contains all the vertices of $$\Gamma$$.  If $$H$$ has a cycle, we can pick any edge $$e$$ of that cycle and delete it, and $$H$$ will still be connected: any path that used $$e$$ can use the rest of the cycle instead.  

Thus, starting from $$G$$, we may repeatedly remove edges from cycles and not disconnect $$G$$ until there are no more cycles left; the result will be a spanning tree.  $$\square$$

Counting trees 
----

It is natural to ask how many trees there are $$n$$ vertices.  If we do not label the vertices, we are asking about isomorphism classes of trees with $$n$$ vertices, and there is no nice known formulas in this case.  If, however, we label the vertices with the numbers from 1 to n, and consider labeled trees, 


Example: 
====

There is only one labeled tree with 2 vertices.  However, there are 3 labeled trees with 3 vertices: any tree with 3 vertices is the path of length 3; all that matters is the label of the central vertex.  

To count the labeled trees on 4 vertices, not there are two possible underlying unlabelled trees: a chain of 4 vertices, or one central vertex of degree 3, adjacent to the others (the structure of the carbon atoms in butane and isobutane, respectively).  

There are 4! ways to label the first chain of vertices, but we can always reverse the order to get the same labelled tree -- i.e., 1-2-3-4, reversed, gives 4-3-2-1.  This gives 12 labelled trees with the chain as their underlying unlabelled tree.

To label the $$T$$ tree, note that all 3 vertices of degree 1 are interchangable.  Thus, all that matters is the label on the central vertex, which can be any number from 1-4, and so there are 4 ways to label the second tree.


Theorem (Cayley) 
===
There are $$n^{n-2}$$ labelled trees on $$n$$ vertices.

We will prove Cayley's result in the next lecture.
