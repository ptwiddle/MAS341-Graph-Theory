---
layout: lecture
title: Lecture 11&#58; Routing algorithmns -- Dijkstra's and A* 
comments: True
---

Today we will discuss two related algorithms for finding the shortest path between two points in a weighted graph, Dijkstra's algorith, which has been taught in this module for years, and the A* algorithm, which is a tweak on Djikstra's algorithm that hasn't been in this module before.

Both algorithms are extremely standard and there are a wealth of online examplesand comparison videos and information that should be valuable:

Djikstra: [Wikipedia](https://en.wikipedia.org/wiki/Dijkstra's_algorithm) [Computerphile video](https://www.youtube.com/watch?v=GazC3A4OQTE) 

A*: [Wikipedia](https://en.wikipedia.org/wiki/A*_search_algorithm) [Computerphile video](https://www.youtube.com/watch?v=ySN5Wnu88nE)

Dijkstra's Algorithm
----

Dijkstra's algorithm finds the shortest path between two points in a weighted graph. There are some variations on it, and the version we present will find the shortest path between a fixed vertex $$v$$ and every other vertex $$a$$ of $$\Gamma$$, which basically all versions do without more work.  We will denote $$c_v(a)$$ to be the cost of the shortest path from $$v$$ to $$a$$.

For Dijkstra's algorithm to work, we require all the edge weights to be non-negative, but in real world examples this is usually true.

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


A* Algorithm
---------

If all you know is that you have a weighted graph, then Dijkstra's algorithm is essentially the best that can be done.  However, in many real life situations more about the structure of the graph is known.

For example, suppose I wanted to drive the shortest path from Sheffield to Edinburgh.  I know that I want to drive mostly North -- I won't be able to drive in a straight line to Edinburgh, and it may be that the fastest trip drives South slightly to get onto a highway -- but in general, I want to be headed North, and I can safely throw out any path that takes me through Nottingham.  However, since Nottingham is closer to Sheffield than Edinburgh is, Dijkstra's algorithm would waste a lot of time exploring the roads around Nottingham.

Similarly video games usually take place on very regular grid-like graphs, where it's very clear what the shortest path would be.  However, there may be obstacles in the way that the shortest path must avoid, which means we can't blindly return one of the regular shortest paths.

We need a way to encode this extra information we know about the graph.  In the A* algorithm this is done through a heuristic function.

Definition
====

A *heuristic function* $$h(v,w)$$ takes in two vertices $$v, w$$, and returns a guess at the distance from $$v$$ to $$w$$.  We say that a heuristic is *admissible* if the guess is always strictly less than the shortest path from $$v$$ to $$w$$ in the graph.

The A* algorithm will make use of a heuristic algorithm to priotize the search direction.  If the heuristic is admissible, the algorithm will be guaranteed to return a shortest path.    This will no longer be true if the heuristic is not admissible.

The "better" the heuristic, the faster the algorithm will run -- if the heuristic function $$h(v,w)$$ returns the actual distance of the shortest path from $$v$$ to $$w$$, then the algorithm will immediately find the optimal path.  Sometimes it is convenient to use a non-admissible, but "close to" admissible heuristic in situations where speed is important -- for instance, in a video game where hundreds of characters are moving simultaneously.




The A* algorithm
====
The goal is to find the shortest path from $$s$$ to $$f$$ (for start and finish) in a weighted graph, using some heuristic function $$h(v,w)$$.  The algorithm is quite similar to Dijkstra's: at all times we will have a list of "known" shortest paths from $$s$$ to other vertices $$v$$, and of candidate shortest paths from $$s$$ to vertices $$w$$, and will continually update our lists by moving the "best" candidate path to a known path.

What changes is what "best" means -- rather than add the vertex with the cheapest distance from $$s$$, that is, the lowest $$d_\Gamma(s,v)$$, we add the vertex with the lowest value of:
 $$f(v)=d_\Gamma(s,v)+h(v,f)$$.
The first part is the actual cost of a path from $$s$$ to $$v$$, the second part is the heuristic cost of a path from $$v$$ to $$f$$.  Thus, the function $$f$$ records our best guess at the cost of a path from $$s$$ to $$f$$ through $$v$$.






