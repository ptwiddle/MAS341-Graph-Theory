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


The exam will consist of four equally weighted questions, all mandatory.  The four questions are on: Introductory matters, algorithms, graphs on surfaces, and colourings.  Each question consists of multiple parts.  The four questions may not appear in the order we covered them in lecture.

I've given lists of usual question types that appear in each section.  These lists are not necessarily exhaustive, but anything not appearing in the list would most likely be both part of the 20 percent of the exam that's "difficult", and a variation/exension of a question type that **is** on the list.


Question 1: Introductory matters
====
In general, this covers everything we did up to when we began algorithms, and is the material in Sections 1 and 2 of the notes, and is unaffected by the strike.

Questions are almost entirely from the following:
 - Solving or proving insolvability of Instant insanity cubes
 - Proving a graph is or is not (semi)-Eulerian i.e., using and proving Euler's Theorem
 - Proving a graph is or is not (semi)-Hamiltonian (case by case, a few tricks, proof for Peterson graph)
 - Definition of a tree, proving trees have leaves, and that a tree on $$n$$ vertices has $$n-1$$ edges
- Degrees of vertices, the handshaking lemma, and basic applications to chemistry
 - Proving two graphs are or are not isomorphic.



Question 2: Algorithms
====

This is section 3 of the notes, and was the material covered around the strike.  We skipped one topic traditionally covered -- finding longest paths, and applications of this to scheduling problems.  We also skipped some proofs of material in this section, but I don't believe the proofs skipped have typically appeared on exams anyway.

Additionally, Prim's algorithm is a new topic that had not appeared in previous years, when only Kruskal's was covered.

Questions are almost entirely from the following:
 - Using Prim's or Kruskal's algorithm for finding the cheapest weight spanning tree; analysing if there is a unique such tree or more than one
 - Using Dijkstra's algorithm for finding shortest paths between points; what happens if we change edge lengths -- does the shortest path get longer?
 - Traveling Salesman problem: statement, nearest neighbor greedy algorithm for upper bound, finding lower bounds for TSP by considering spanning trees
  - Prüfer code: going back and forth from a labelled tree and its code; Cayley's Theorem that there are $$n^{n-2}$$ labelled trees on $$n$$ vertices.

The only algorithm I would ask you to prove works as advertised is the lower bound for the Travelling Salesman problem.  In particular, I will *not* ask you to prove Prim, Kruskal's or Dijkstra's algorithm works.

Question 3: Graphs on Surfaces
===
This is Section 4 of the notes, and this material was covered after the strike and is unaffected by it -- I was hoping to have slightly more time on it than we did, but we have the same amount that has been spent in past years.

Questions are almost entirely from the following:
 - Planarity Algorithm for Hamiltonian graphs, in particular proving $$K_{3,3}$$ and $$K_5$$ aren't planar
 - Kuratowski's Theorem characterising planar graphs: stating it, and using and proving the "easy" direction, i.e., that if a $$G$$ has a subgraph $$H$$ that's a subdivision of $$K_{3,3}$$ or $$K_5$$ then $$G$$ isn't planar.
 - Other surfaces: Drawing graphs on the Mobius band and on the torus.  Note: in some previous years there have been questions involving the real projective plane $$\mathbb{RP}^2$$ or the Klein bottle; we did *not* cover that this year and it won't be required
 - Euler's Theorem $$v-e+f=2$$ for planar graphs: proving it and using applications of it.  We did a slightly different proof of Euler's theorem this year than in previous years.  Asking you to prove it is still fair game, but the solutions given in any practice exams may look unfamiliar.


Question 4: Colourings
===

This is Section 5 of the notes, and is the material we will cover in the next two weeks; this material is unaffected by the strike.

Questions are almost entirely from the following:
 - Chromatic number of a graph: definition, determining the chromatic number for a particular graph with proof, proving chromatic number is at most the maximum degree plus one, word problem applications
 - Chromatic Index of a graph: definition, determing the chromatic index of a particular graph with proof, word problem applications; stating Vizing's theorem
 - Chromatic Polynomial: definition, deletion-contraction, proving it's a polynomial, recovering chromatic number, number of vertices, number of edges from it.
 - Calculating Chromatic Polynomial of a graph, using: deletion contraction / induction / gluing along a vertex or an edge

Old exams and solutions
----
I've included links to the last three years exams, and a mock practice exam I wrote up a few years ago.  Note that before last year the exam format was five questions, choose four.  I've looked over the exam and given some comments below on what material is not fair game for this year; I believe I've caught it all, but let me know if you think I've missed something.


<a href="../GraphTheory2017.pdf"> 2017 Exam </a> and <a href="../GT2017Solutions.pdf"> Solutions </a>
===
- **2.i and 2.ii:** We didn't cover longest paths, so skip this question; replace it with a Dijkstra's question
- **3.iv:** Replace "Projective plane" with "Mobius band"

<a href="../GraphTheory2016.pdf"> 2016 Exam </a> and <a href="../GT2016Solutions.pdf"> Solutions </a>
===
- **2.ii:** We skipped longest paths, this question is not applicable.
- **4.i:** Replace "projective plane" with "Mobius band"
- **4.ii:** We didn't discuss Euler characteristic of arbitrary surfaces.  Replace it with "State Euler's theorm for graphs drawn on the sphere, and prove it."

 <a href="../GraphTheory2015.pdf"> 2015 Exam </a> and <a href="../GT2015Solutions.pdf"> Solutions </a>
===
- **1.i:** Skip; it's an application we didn't cover (though it's not hard)   
- **2.i:** Use the nearest neighbour heuristic (the nearest-insertion heuristic is a bit more complicated and we didn't cover)
- **3.i:** This question wouldn't appear on the exam, because we didn't phrase anything quite this way, but it's basically doable from what we've done if you want to think about it.

<a href="../PracticeExam.pdf"> An old practice exam </a> and <a href="../PracticeSolutionsFixed.pdf"> solutions </a>
===
- **2.iii:** Replace with "State Euler's Theorem on planar graphs."
- **2.iv:** Replace with "Using Euler's Theorem for planar graphs, give another proof that $$K_{3,3}$$ isn't planar"
- **3.i:** Just do shortest path for a; and hence skip b


 




