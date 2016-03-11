---
layout: lecture
title: Lecture 10&#58; Kruskal's algorithm	
comments: True
---

Kruskal's algorithm
----

We now present Kruskal's algorithm, which solves the problem of finding a minimal weight spanning tree in a weighted graph $$\Gamma$$.  Before discussing the algorithn, let's look at a toy example to get an idea of the problem.

Example
===

Consider the following weighted graph:

<a href="http://www.presheaf.com/?d=d4j1dh1n5r454664y4r70405p273k5c"><img src="http://presheaf.com/cache/d4j1dh1n5r454664y4r70405p273k5c.png" title="click to go to presheaf.com for editing"/></a>

Obviously, there are three spanning trees, obtained by removing one of the three edges.  The spanning tree A-B-C has weight 7, B-C-A has weight 6, C-A-B has weight 5, and so we have found the cheapest spanning tree.


Any finite graph will only have finitely many spanning trees, and so it is always possible to exhaustively find all of them, compute their weights, and hence find the cheapest.  However, for large graphs there will be many spanning trees.  For example, a spanning tree of the complete graph $$K_n$$ is equivalent to a labelled tree on $$n$$ vertices, and by Cayley we know there are $$n^{n-2}$$ of these trees, which grows faster than exponential or factorial!  Thus, in practice, to find a minimal spanning tree we need a more efficient algorithm than brute forst checking all the possibilities.


Kruskal's algorthm
===

For finding spanning trees, it turns out there are several easy algorithms that will always find the cheapest spanning tree.  Many of them are *greedy algorithms*, which do not "plan ahead", but rather blindly do the best possible next step.  Kruskal's algorithm is an example of these, which builds a spanning tree $$T$$ step by step, starting from the subgraph of $$\Gamma$$ consisting just of the vertices of $$\Gamma$$ and no edges:

1. Find the cheapest edge $$e$$ remaining from $$\Gamma$$, and remove it from $$\Gamma$$.
2. If adding $$e$$ to $$T$$ will not make any loops, add it to $$T$$.  Otherwise, discard it.
3. Iterate the first two steps until $$T$$ is a spanning tree.

 In class we now ran an example of Kruskal's algorithm -- we'll skip that in the note, but there are many such examples available online, for instance, in <a href="https://www.youtube.com/watch?v=71UQH7Pr9kU"> this short Youtube video </a>.

Note that to have a spanning tree, the graph $$\Gamma$$ must be connected.  Running Kruskal's algorithm on a disconnected graph will produce a spanning tree for each component of $$\Gamma$$.

Proof of the correctness of Kruskal's algorithm:
===

From a mathematical point of view, the interesting part is to prove that running Kruskal's algorithm on a connected graph will always produce a minimal spanning tree.  There are two things to prove: that the end result of Kruskal's algorithm actually is a spanning tree, and that it is a minimal cost spanning tree.

To prove the first part, we first note that the graph $$T$$ produced by Kruskal's algorithm contains all the vertices of $$\Gamma$$, as they were all added at the beginning.  Thus, we only have to show that $$T$$ is a tree -- that is, it is connected, and that it has no cycles.

Suppose that $$T$$ consisted of more than one component.  Since $$\Gamma$$ is connected, there would be two components of $$T$$, say, $$C_1$$ and $$C_2$$, with edges between $$C_1$$ and $$C_2$$.  But adding the cheapest such edge to $$T$$ does not create any loops, and hence it would have been added by Kruskal's algorithm, a contradiction.

It is immediate that $$T$$ will not have any loops, because Kruskal's algorithm checks to make sure no loops are created before it adds an edge.  Thus, the output of Kruskal's algorithm is always a spanning tree.

We now prove that this spanning tree always has minimal weight.  We do this by inductively proving that after each step of the algorithm, the graph $$T$$ we have produced is contained in *some* minimal spanning tree.  

The base case is clear: any minimal spanning tree contains all the vertices of $$\Gamma$$, which is the initial graph $$T$$, and since $$\Gamma$$ is finite there exists *some* minimal spanning tree.

Now, suppose that we are in the middle of running Kruskal's algorithm, know the graph $$T$$ we currently have is contained in a minimal spanning tree, and are about to add the edge $$e$$ to $$T$$.  We need to prove that the result $$T\cup e$$ will also be contained in a minimal spanning tree.

Let $$M$$ be a minimal spanning tree that contains $$T$$; if $$M$$ also contains $$e$$, we are done, and so we suppose that $$M$$ does not contain $$e$$.  That means that adding the edge $$e$$ to $$M$$ must create a cycle $$C$$.  Since $$T\cup e$$ does not contain any cycles, there must be some edge $$f$$ that is in $$C$$ but not in $$T$$.

Thus, we see that $$M^\prime =(M\setminus f) \cup e$$ is a spanning tree that contains $$T\cup e$$.  We claim that $$M^\prime$$ is also a minimal weight spanning tree.  So $$M$$ and $$M^\prime$$ differ only in the edges $$e$$ and $$f$$, we have to show $$w(e)=w(f)$$.  Since $$M$$ is by supposition a minimal weight spanning tree, we have that $$w(f)\leq w(e)$$.  Since Kruskal's algorithm is trying to add the edge $$e$$ instead of $$f$$, we have that either $$w(e)\leq w(f)$$, or that adding $$f$$ to $$T$$ creates a cycle.  But $$T\cup f\subset M$$ which is a tree, so it cannot be creating a cycle, and we must have that $$w(e)=w(f)$$, and so $$M^\prime$$ is a minimal weight spanning tree that contains $$T\cup e.  \square$$



Comments on minimal spanning trees
===

Although Kruskal's algorithm only finds a single minimal spanning tree, the only time Kruskal's algorithm has any choice is in what order to add edges with the same weight.  Thus, it is possible to find all minimal spanning trees by analyzing what happens when we had a choice of edges to add.

There are several other algorithms for finding minimal spanning trees:

1. [Prim's algorithm](https://en.wikipedia.org/wiki/Prim%27s_algorithm) is very similar to Kruskal's algorithm, but we start from a single vertex, and always add the cheapest edge that is connected to what we already have and doesn't create any loops.
2. The [Reverse-delete algorithm](https://en.wikipedia.org/wiki/Reverse-delete_algorithm) is the opposite of the greedy algorithm.  Rather than adding the cheapest edge possible, the Reverse-delete algorithm worries about getting "stuck" having to add an expensive edge.  It continually finds the most expensive edge.  If removing that edge does not disconnect the graph, it does so.  If it does disconnect the graph, it keeps that edge as part of the spanning tree, and finds the next most expensive edge.

