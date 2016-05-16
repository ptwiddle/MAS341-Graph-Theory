---
layout: lecture
title: Lecture 11&#58; Traveling Salesman; Dijkstra's algorithm	
comments: True
---

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

Dijkstra's Algorithm
----

Dijkstra's algorithm finds the shortest path between two points in a weighted graph; there are some variations on it, and the version we present will find the shortest path between a fixed vertex $$v$$ and every other vertex $$a$$ of $$\Gamma$$.  We will denote $$c_v(a)$$ to be the cost of the shortest path from $$v$$ to $$a$$.

The algorithm
===

The basic set-up of the algorithm is to keep a running a list of "potential" shortest paths between $$v$$ and some of the vertices.  To initialize this list, we just record every vertex $$a$$ adjacent to $$v$$, and the weight of the edge $$vw$$ connecting them.  

At each step of the algorithm, we choose the lowest such "potential" shortest path, say, a path to $$a$$, and declare it to actually be the shortest path.  We then update our list of potential shortest paths by looking at all vertices $$b$$ adjacent to $$w$$.  We could get a path from $$v$$ to $$b$$ by first taking a path from $$v$$ to $$a$$, which costs $$c_v(a)$$, and then adding on the edge from $$a$$ to $$b$$, which costs $$w(ab)$$.  Thus, we compare the cost of the "potential" shortest path from $$v$$ to $$b$$ (if there is one), with $$c_v(a)+w(a-b)$$, and make whichever one is lower the new potential cheapest path from $$v$$ to $$b$$.  We then remove $$a$$ from the list of vertices, and continue on our way.


Proof of correctness
===

Unlike Kruskal's algorithm, where we had to do some work to prove that the algorithm always produced the correct answer, with Dijkstra's algorithm it is fairly obvious that it will always give the correct answer.  Consider the step where we final a potential shortest path from $$v$$ to $$a$$ as actually being the shortest.  If this wasn't true, then there would be some shorter path from $$v$$ to $$a$$.  We haven't found this path yet, which means it would have to travel through some other vertex $$b$$ we haven't yet optimized the minimal path for.  But any path from $$v$$ to $$b$$.  But since the cost of the path from $$v$$ to $$a$$ is minimal among potential paths we can see, the cost of the path from $$v$$ to $$b$$ would be at least as much as the cost to $$v$$ to $$a$$, and that's before we add the extra cost from $$b$$ to $$a$$.


Examples
===

There are [many](https://www.youtube.com/watch?v=0nVYi3o161A) [videos](https://www.youtube.com/watch?v=WN3Rb9wVYDY) online demonstrating Dijkstra's algoirth, as well as some [applets](http://optlab-server.sce.carleton.ca/POAnimations2007/DijkstrasAlgo.html)

We did one quick example at the end of class, and will begin the next class working another example, which will get transcribed and discussed in the notes.


