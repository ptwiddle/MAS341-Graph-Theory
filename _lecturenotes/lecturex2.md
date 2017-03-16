---
layout: lecture
title: Lecture 12&#58; Scheduling and longest paths	
comments: True
---


Last session we discussed Dijkstra's algorithm for finding the *shortest* path between two points in a graph.  Our main topic today will be to discuss an algorithm for finding the *longest* path between two points in a graph. 

Before discussing the algorithm, we give some background to motivate the question and to make it well defined.

Directed graphs
-----

The first problem in discussing the longest path in graphs is that it won't exist.  If we are allowed to revist vertices and edges, then we can simply go back and forth between two vertices an arbitrary number of times to make any path as long as we want.  One way to rule this out would be to just not allow repetition of vertices or edges; doing this would make looking for the longest path similar to seeing how close to Eulerian / Hamiltonian the graph is.   This *is* an interesting problem, but is not the problem we consider.

Instead, we will work with a slightly different class of graphs that will make repetition of edges and vertices impossible.

Definition
====
A *directed graph* $$\Gamma$$ is a graph where each edge has a direction.  Rather than simply connecting two vertices, an edge $$e$$ goes *from* vertex $$a$$ *to* vertex $$b$$.  An example is a system of one way roads.

Directed graphs are usually drawn in a similar way to graphs, but with the edges becoming arrows rather than just lines to indicate which way they go:

<image src="../Slides/Pictures/directedgraph.png"></image>

A path in a directed graph is series of edges $$e_1, e_2, \dots, e_n$$ so that the end vertex of $$e_i$$ is the start vertex of $$e_{i+1}$$.

A directed graph is *acyclic* if it has no oriented cycles.  

Scheduling
---

The main application of the longest path algorithm is in scheduling.  Suppose we have a large project -- say, building a house -- that is composed of many smaller projects: digging the foundation, building the walls, connecting to gas, electricity, and water, building the roof, doing the interiors, landscaping, etc.
 
Some of these activities will require others to be done before them (you can't put the roof on before you've built the walls; you don't want to do the landscaping before you've dug your water lines), while others could be done at the same time (finishing the interiors and doing the landscaping).  Each sub-job has an expected amount of time required to finish it; you'd like to know before hand how long the whole task will take, and when the various sub-jobs should be done so you can arrange the contractors.  

From a series of jobs like this, we will construct a weighted, directed, acyclic graph.  The edges will be the sub-jobs. The weights of each edge will be the expected length of time that job has.  The structure of the graph will encode the dependencies of the subjobs on each other -- an edge $$e$$ will flow into an edge $$f$$ if the job $$f$$ immediately depends about the job $$e$$.  The graph will be acyclic, because any cycle would be a chain of events that each depended on the previous one, which would mean the job could never be started!

We will work out the construction of this graph in one example.  It is not always trivial to construct the directed graph from the table of jobs and dependencies.  It is not clear what the vertices should be, and sometimes dummy edges and vertices need to be encoded.  You do not need to worry about constructing these graphs in general, though if you're curious it can be interesting to think about.  Any exam question about this topic would supply you with the directed graph.

Example
===

Consider the following table, listing tasks $$A-H$$, the expected time of completion for each task, and the required tasks before a given task can be started.

<table>
<tr>
<td> Task </td> <td> Time </td> <td> Prerequisites </td> </tr>
<tr> <td> A </td> <td> 6 </td> <td> </td> </tr>
<tr> <td> B </td> <td> 7 </td> <td> </td> </tr>
<tr> <td> C </td> <td> 4 </td> <td> A </td> </tr>
<tr> <td> D </td> <td> 3 </td> <td> A </td> </tr>
<tr> <td> E </td> <td> 4 </td> <td> B,D </td> </tr>
<tr> <td> F </td> <td> 10 </td> <td> C </td> </tr>
<tr> <td> G </td> <td> 3 </td> <td> C </td> </tr>
<tr> <td> H </td> <td> 10 </td> <td> E,G </td> </tr>
</table>

Here is the corresponding graph encoding this information:
<image src="../Slides/Pictures/tasks.png"></image>

Construction of the graph
====

We outline how the graph above was constructed.  We make one vertex for the start, one vertex for the finish, and then another vertex for each set of dependencies, that is, the entries in the third column.  Then we draw an edge for each letter, beginning at the vertex corresponding to its set of prerequisites (or the start, if it has none), and ending at the vertex that contains it as a prerequisite (or the end, if no tasks require it as a prerequisite).

Note that this method works only if any two sets of prerequisites either have nontrivial intersection or are identical.  The tricky cases you don't have to worry about are when this isn't true.  

Longest Paths
----

With that detour out of the way, we see why finding the longest path in a directed acyclic graph is useful: in case the edges are tasks and the weights are expected times, the length of the longest path is the minimal time the whole project would be able to be completed.

Moreover, it is useful to actually know what the longest paths are -- to achieve this minimal time, each task in the longest path must be completed in the expected amount of time, and the next task in the path must be started immediately when the first one finishes.  For this reason, the longest paths are known as *critical paths*.  

Longest path algorithm
====

We now describe an algorithm for finding the longest paths from a starting vertex $$S$$ to all other vertices.

First, number the vertices of your graph is that all edges flow from a lower vertex to a higher vertex.  This is always possible for an acyclic graph, but not necessarily uniquely so -- the vertex numbering in our example graph satisfies this property,  but we could have switched the labelling of vertices two and three and still had the desired property.

Then, we find the longest path to each other vertex inductively, by ordering of their numbers.  Suppose that we have found the longest paths to each vertex with number lower than $$k$$, and we want to find the length of the longest path to vertex $$k$$, which we will call $$u$$.

  Let $$e_i$$ be the edges that come into $$u$$, let $$w(e_i)$$ be the lengths of these edges, and let $$v_i$$ be the source vertex of $$e_i$$.  Since our edges go from lower numbered vertices to higher numbered vertices, all the $$v_i$$ are labelled with numbers lower than $$w$$ (i.e., lower than $$k$$), and hence by the inductive hypothesis we know the longest paths to $$v_i$$.   Let $$\ell(v_i)$$ be the length of this longest path from $$S$$ to $$v_i$$.

Any path to $$w$$ must pass through one of the $$v_i$$, and so the length of the longest path to $$u$$ is the 

$$\ell(u)=\text{max}_i \big[\ell(v_i)+w(e_i)\big]$$


Typically we will want to find the longest path in addition to just knowing its length, and an easy way to do this is to record the edges $$e_i$$ that achieve the maximum.  Then we can find the long paths in reverse by starting from $$F$$ and going to any recorded vertex.


Example of the algorithm
====

We illustrate the longest path algorithm with our example graph.  Our start vertex is $$S$$, and so $$\ell(S)=0$$.

Vertex 1 has only one incoming edge: $$A$$, with weight 6, and so $$\ell(1)=6+\ell(S)=6$$.

Vertex 2 has two incoming edges: $$B$$ and $$D$$, and so we see that $$\ell(2)$$ is the maximum of $$w(D)+\ell(1)=3+6=9$$, and $$w(B)+\ell(S)=7+0=7$$, and so $$\ell(2)=9$$.  

Vertex 3 has just one incoming edge: $$C$$, and so $$\ell(3)=w(C)+\ell(1)=4+6=10$$.  

Vertex 4 has two incoming edges: $$G$$ and $$E$$, and so $$\ell(4)$$ is the maximum of $$w(G)+\ell(3)=3+10=13$$ and $$w(E)+\ell(2)=4+9=13$$.  Thus, the maximum is achieved in two different ways, and we see that there are two paths of length 13 from $$S$$ to $$4$$ -- $$S-1-3-4$$ and $$S-1-2-4$$.  

Finally, vertex $$F$$ has two incoming edges, $$F$$ and $$H$$, and so $$\ell(F)$$ is the maximum of $$w(F)+\ell(3)=10+10=20$$ and $$w(H)+\ell(4)=10+13=23$$.  There are two paths that achieve this maximum -- $$A-C-G-H$$ and $$A-D-E-H$$.  

Critical path analysis
====

Apart from knowing the minimum time for completion of the project, finding the longest paths is useful for analysing where to put resources.  In particular, which tasks, if they run slightly over, would make the whole project run late?  Which tasks, if they were able to finish slightly early, would make the whole project finish early?

To make the whole project run later, we need to increase the length of the longest path, which means we to increase the length of *any* long path.  Thus, the edges that would make the whole project run over are those contained in *any* longest path -- in our graph, these are edges $$A,C,D,E, G$$ and $$H$$.  

To make the whole project finish early, we need to decrease the length of *every* longest path, and so these are the edges that are included in *every* longest path. In our graph, these are edges $$A$$ and $$H$$.

These ideas can be developed further, to list for each task the earliest possible starting time, and the latest starting time that is possible while still finishing the whole project in the minimum amount of time.


