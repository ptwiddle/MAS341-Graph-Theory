---
layout: lecture
title: Lecture 10&#58; Kruskal proof, Traveling Salesman
comments: True
---

Kruskal's completed:
=====

In this morning's lecture we described Kruskal's algorithm for finding a minimal weight spanning tree in a weighted graph.  After demonstrating the algorithm, we showed that it always produces a spanning tree, but we have not yet shown that this spanning tree has minimal weight.  We do that now.


The proof will be inductive.  Let $$T_0$$ be the subgraph that Kruskal's algorithm starts with, namely, all the vertices of $$\Gamma$$ and none of the edges.  Let $$T_k\subset\Gamma$$ be the subgraph Kruskal's produces after adding $$k$$ edges to $$T_0$$.  We willinductively prove that $$T_k$$ is contained in *some* minimal spanning tree of $$\Gamma$$.  In particular, since we know $$T_{n-1}$$ is a spanning tree, we see that $$T_{n-1}$$ will be a minimal weight spanning tree.  

The base case is clear: any minimal spanning tree contains all the vertices of $$\Gamma$$, which is the initial graph $$T_0$$, and since $$\Gamma$$ is finite there exists *some* minimal spanning tree.

For the inductive step, we assume that $$T_k$$ produced from Kruskal's algorithm is contained in some minimal spanning tree $$M$$, and Kruskal's algorithm tells us we should construct $$T_{k+1}$$ from $$T_k$$ by adding the edge $$e$$ to $$T$$.  We need to prove that $$T_{k+1}$$ is contained in some minimal weight spanning tree $$M^\prime$$.  We claim we can take $$M^\prime=M\setminus\{e\}\cup\{f\}$$.

First, note that $$M^\prime$$ is indeed a spanning tree; since $$M\cup e$$ has a cycle, $$M^\prime$$ is connected, and it has the right number of edges.

Now, we must show $$M^\prime$$ has minimal weight.  Since $$M^\prime$$ only differs from $$M$$ (which had minimal weight) by adding $$f$$ and removing $$e$$, we see that $$w(M^\prime)=w(M)$$ if and only if $$w(e)=w(f)$$.

Since $$M$$ is by supposition a minimal weight spanning tree, we have that $$w(f)\leq w(e)$$.  Since Kruskal's algorithm is trying to add the edge $$e$$ instead of $$f$$, we have that either $$w(e)\leq w(f)$$, or that adding $$f$$ to $$T$$ creates a cycle.  But $$T\cup f\subset M^\prime$$ which is a tree, so it cannot be creating a cycle, and we must have that $$w(e)\leq w(f)$$.


Thus, $$w(e)=w(f)$$, and so $$M^\prime$$ is a minimal weight spanning tree that contains $$T\cup e.  \square$$



Comments on minimal spanning trees
===

Although Kruskal's algorithm only finds a single minimal spanning tree, the only time Kruskal's algorithm has any choice is in what order to add edges with the same weight.  Thus, it is possible to find all minimal spanning trees by analyzing what happens when we had a choice of edges to add.

There are several other algorithms for finding minimal spanning trees:

1. [Prim's algorithm](https://en.wikipedia.org/wiki/Prim%27s_algorithm) is very similar to Kruskal's algorithm, but we start from a single vertex, and always add the cheapest edge that is connected to what we already have and doesn't create any loops.
2. The [Reverse-delete algorithm](https://en.wikipedia.org/wiki/Reverse-delete_algorithm) is the opposite of the greedy algorithm.  Rather than adding the cheapest edge possible, the Reverse-delete algorithm worries about getting "stuck" having to add an expensive edge.  It continually finds the most expensive edge.  If removing that edge does not disconnect the graph, it does so.  If it does disconnect the graph, it keeps that edge as part of the spanning tree, and finds the next most expensive edge.




Traveling Salesman Problem
---

The *Traveling Salesman Problem*, abbreviated TSP, is the following: given a weighted graph $$\Gamma$$, find the cheapest Hamiltonian path; that is, the cheapest closed walk on $$\Gamma$$ that visits every vertex exactly once.

We begin with some basic observations:

-  It is enough to consider the complete graph $$K_n$$.  If we are given some other weighted graph $$\Gamma$$, we can add all the edges not in $$\Gamma$$ but make their weights *much* larger than any of the weights inside $$\Gamma$$.

- The problem of determining whether a given graph $$\Gamma$$ has a Hamiltonian cycle is a special case of the traveling salesman problem.  To see this, suppose we're given a graph $$\Gamma$$, and we want to determine whether it is Hamiltonian.  We create a weighted $$K_n$$, with vertices the vertices of $$\Gamma$$ by giving the edge $$v-w$$ a very small weight $$\epsilon$$ if $$v$$ and $$w$$ *are* adjacent in $$\Gamma$$, and a very large weight $$M$$ if $$v$$ and $$w$$ *are not* adjacent in $$\Gamma$$.  Then, any Hamiltonian path in $$\Gamma$$ would have cost $$n\epsilon$$, where as any path that uses an edge not in $$\Gamma$$ costs more than $$M$$.  So, if we make $$M>n\epsilon$$, the TSP for our weighted $$K_n$$ will have a solution with cost less than $$M$$ if and only if $$\Gamma$$ had a Hamiltonian cycle.

Since determining whether a graph $$\Gamma$$ is Hamiltonian is difficult (NP complete), the TSP will also be.  As such, we will not discuss any algorithms for actually solving TSP.  Instead, we will discuss methods for giving upper and lower bounds for the TSP.

Upper bounds for TSP
====

Since the TSP asks for the cheapeast Hamiltonian cycle, taking *any* Hamiltonian cycle and calculating its cost will be an upper bound for the TSP.  Just choosing a random Hamiltonian cycle will in general be very expensive and silly -- for instance, going from Sheffield to London to Rotherham to Edinburgh to Chesterfield to Glasgow to Nottingham to Brighton is clearly not optimal.

A greedy algorithm will give a heuristically better result: we call it the *nearst neighbor algorithm*.  At each step, simply go to the nearest city you have not already visited.  This will give good results at the beginning, but since we do not do any planning ahead, it will in general give bad results, as the following example illustrates:

<a href="http://presheaf.com/?d=di3d5c2w4p5r4v5j31382bn3c1643l"><img src="http://presheaf.com/cache/di3d5c2w4p5r4v5j31382bn3c1643l.png" title="click to go to presheaf.com for editing"/></a>

Consider running the Nearest Neighbor algorithm starting at $$v_0$$.  At the first step, we have a choice -- we could go to $$v_1$$ or to $$v_9$$.  Suppose we go to $$v_1$$.  After that, our choice is forced -- $$v_1-v_2-v_3-v_4-v_5-v_6-v_7-v_8-v_9$$ costs one at each step.  Now, we still have to visit $$T$$ before returning to $$V_0$$, which will cost us 10 to detour through.  We clearly should have planned ahead and visited $$T$$ in between vertices $$v_4$$ and $$v_5$$ at a cost of 4. 

The nearest neighbour algorithm for finding upper bounds is demonstrated in [this video](https://www.youtube.com/watch?v=wRvQSLtRnz0).

Clearly the nearest neighbour algorithm is not very good, and better algorithms are possible; we present it first to give a quick but reasonable way to get a solution to TSP that isn't *completely* horrible, and second to illustrate that greedy algorithms in general will not be efficient.


Lower bounds for TSP
===

To get a lower bound for TSP we have to be a little more intelligent.  Suppose we had a solution $$C$$ to the TSP for $$\Gamma$$, and that we deleted one vertex $$v$$ from $$C$$.  Deleting a vertex from a cycle gives us a path $$P$$, and in particular a tree.  Furthermore, $$P$$ visits every vertex in $$\Gamma$$ except for $$v$$, and so it is a spanning tree of $$\Gamma\setminus v$$.  

We can use Kruskal's algorithm (or another) to find a minimal spanning tree $$T$$ of $$\Gamma\setminus v$$, and we have that $$w(P)\geq w(T)$$.  The cycle $$C$$ contains just two more edges, from $$v$$ to two other vertices, say $$a$$ and $$b$$.  We can obtain lower bounds on the weights of the edges $$v-a$$ and $$v-b$$ by taking the weights of the lowest two edges out of $$v$$, maybe $$e_1$$ and $$e_2$$.  We have

$$w(C)=w(P)+w(a-v)+w(b-v)\geq w(T)+w(e_1)+w(e_2)$$

giving us a lower bound on solutions to the TSP.

This method of finding lower bounds is illustrated in [this video](https://www.youtube.com/watch?v=NA2RToI4-ro)


