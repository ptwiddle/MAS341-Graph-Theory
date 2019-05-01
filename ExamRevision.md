---
layout: page
title: Revision
permalink: /Exam-Revision/
---

This page is a brief discussion of the exam and some material to prepare for it, including coverage and some discussion of old exams.

[List of Proofs](../Proofs/)
===

This is essentially contained within the discussion of the exam found below, but some people find it useful to find them listed in one place: a list of proof type questions that could appear on the exam, and a few that definitely won't.

Exam Structure 
----

The exam will consist of four equally weighted questions, all mandatory.  The four questions are on: Introductory matters, algorithms, graphs on surfaces, and colourings.  The four homework assignments should give a good first approximation of what these questions will be like.  Each question consists of multiple parts.  The four questions may not appear in the order we covered them in lecture.

I've given lists of usual question types that appear in each section.  These lists are not necessarily exhaustive, but anything not appearing in the list would most likely be both part of the 20 percent of the exam that's "difficult", and a variation/exension of a question type that **is** on the list.

The last two or three years of exams required very little curving, and the overall difficulty level of this years exam should be about the same.  However, there have been a few too many extremely high and extremely low marks, so there should be more "easy" and more "hard" marks on this year's exam.  The standard targets are 40% "easy" marks and 20% "hard" marks.


Question 1: Introductory matters
====
In general, this covers everything we did up to when we began algorithms, and is the material in Sections 1 and 2 of the notes.

Questions are almost entirely from the following:
 - Solving or proving insolvability of Instant insanity cubes
 - Proving a graph is or is not (semi)-Eulerian i.e., using and proving Euler's Theorem
 - Proving a graph is or is not (semi)-Hamiltonian (case by case, a few tricks, proof for Peterson graph)
 - Definition of a tree, proving trees have leaves, and that a tree on $$n$$ vertices has $$n-1$$ edges
- Degrees of vertices, the handshaking lemma, and basic applications to chemistry
 - Proving two graphs are or are not isomorphic.



Question 2: Algorithms
====

This is section 3 of the notes.  Students usually find this the easiest, and in an effort to have more easy points on the exam this section might be slightly easier than past exams, which struggled a bit to find a hard part.  Note in revising that Prim's algorithm only started being covered last year; in previous years only Kruskal's was covered.

Questions are almost entirely from the following:
 - Using Prim's or Kruskal's algorithm for finding the cheapest weight spanning tree; analysing if there is a unique such tree or more than one
 - Using Dijkstra's algorithm for finding shortest paths between points; what happens if we change edge lengths -- does the shortest path get longer?
 - Using the longest path algorithm to find the longest path between points; what happens if we change edge lengths?
 - Traveling Salesman problem: statement, nearest neighbor greedy algorithm for upper bound, finding lower bounds for TSP by considering spanning trees
  - Prüfer code: going back and forth from a labelled tree and its code; Cayley's Theorem that there are $$n^{n-2}$$ labelled trees on $$n$$ vertices.

The only algorithm I would ask you to prove works as advertised is the lower bound for the Travelling Salesman problem.  In particular, I will *not* ask you to prove Prim, Kruskal's or Dijkstra's algorithm works.

Question 3: Graphs on Surfaces
===
This is Section 4 of the notes.

Questions are almost entirely from the following:
 - Planarity Algorithm for Hamiltonian graphs, in particular proving $$K_{3,3}$$ and $$K_5$$ aren't planar
 - Kuratowski's Theorem characterising planar graphs: stating it, and using and proving the "easy" direction, i.e., that if a $$G$$ has a subgraph $$H$$ that's a subdivision of $$K_{3,3}$$ or $$K_5$$ then $$G$$ isn't planar.
 - Other surfaces: Drawing graphs on the Mobius band and on the torus.  Note: in some previous years there have been questions involving the real projective plane $$\mathbb{RP}^2$$ or the Klein bottle; we did *not* cover that this year and it won't be required
 - Euler's Theorem $$v-e+f=2$$ for planar graphs: proving it and using it in applications.  A heads up that different years have done different proofs of Euler's theorem, so solutions given in practice exams may look unfamiliar.

Question 4: Colourings
===

This is Section 5 of the notes.

Questions are almost entirely from the following:
 - Chromatic number of a graph: definition, determining the chromatic number for a particular graph with proof, proving chromatic number is at most the maximum degree plus one, word problem applications
 - Chromatic Index of a graph: definition, determing the chromatic index of a particular graph with proof, word problem applications; stating Vizing's theorem
 - Chromatic Polynomial: definition, deletion-contraction, proving it's a polynomial, recovering the chromatic number, number of vertices, number of edges from it.
 - Calculating Chromatic Polynomial of a graph, using: deletion contraction / induction / gluing along a vertex or an edge

Old exams and solutions
----
I've included links to the last three exams and solutions, and a mock practice exam I wrote up a few years ago.  Note that before last year the exam format was five questions, choose four.  I've looked over the exam and given some comments below on what material is not fair game for this year; I believe I've caught it all, but let me know if you think I've missed something.

<a href="../GraphTheory2018.pdf"> 2018 Exam </a> and <a href="../GT2018solutions.pdf"> Solutions </a>
===

<a href="../GraphTheory2017.pdf"> 2017 Exam </a> and <a href="../GT2017Solutions.pdf"> Solutions </a>
===
- Note: The pdf of solutions says 2016, but it is in fact the right set of solutions.
- Question two gives a list of tasks and times -- we didn't cover how to turn this into a directed graph, and you won't have to do this on the exam.  The directed graph is as follows:
![Activity Network for Question 2](../Q2.png)
- **3.iv:** Replace "Projective plane" with "Mobius band"

<a href="../GraphTheory2016.pdf"> 2016 Exam </a> and <a href="../GT2016Solutions.pdf"> Solutions </a>
===
- **4.i:** Replace "projective plane" with "Mobius band"
- **4.ii:** We didn't discuss Euler characteristic of arbitrary surfaces.  Replace it with "State Euler's theorm for graphs drawn on the sphere, and prove it."

<a href="../PracticeExam.pdf"> An old practice exam </a> and <a href="../PracticeSolutionsFixed.pdf"> solutions.</a>  A bit messy, and not as close to what the exam will actually be like, but still some useful questions.
===
- **2.iii:** Replace with "State Euler's Theorem on planar graphs."
- **2.iv:** Replace with "Using Euler's Theorem for planar graphs, give another proof that $$K_{3,3}$$ isn't planar"
- **3.ii (a)** "the heuristic algorithm for finding a good upper bound" is the nearest neighbour algorithm for us (they intend a slightly different 
- **5.ii (d)** we didn't talk about this with this language, and unlikely to appear on the exam, but it's asking for the chromatic number of the dual graph of $$H$$.

 




