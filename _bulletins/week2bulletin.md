---
layout: bulletin
title: Week 2 Bulletin
comments: True
---
Morning
------
[slides](../Slides/Lecture3.html)

In the morning, we discussed what is usually considered the birth of graph theory, in the bridges of Konigsberg question.  We defined walks on graphs, and what it meant for a graph to be connected.  We proved Euler's theorem that a connected graph has an Eulerian cycle if and only if every vertex has even degree, and we didn't quite state the analogous theorem semi-Eulerian graphs -- we picked that up at the beginning of the afternoon lecture.

Afternoon
-----
[Slides](../Slides/Lecture4.html)

In the afternoon, we began by briefly reviewing Euler's theorem and finishing it up by stating the analogous result where we don't require the trail that uses every edge to be closed.

We then turned to Hamiltonian cycles.  Although the definition is remarkably similar to Eulerian graphs, it turns to out to be very hard (i.e., NP complete) to determine whether or not a graph is Hamiltonian.  That doesn't mean it isn't possible to do for small graphs, though, and we discussed some ways to do this; we used one of these to prove that the Petersen graph is not Hamiltonian.  We proved Ore's theorem that a graph with "enough" edge is Hamiltonian.