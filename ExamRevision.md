---
layout: default
permalink: /Exam-Revision/
---

This page is a brief discussion of the exam and some material to prepare for it, including coverage and some discussion of old exams.

The exam will consist of four equally weighted questions, all mandatory.  The four questions are on: Introductory matters, algorithms, graphs on surfaces, and colourings.  Each question consists of multiple parts.  The questions may not appear in this order.  Exams before last year did not have this exact format -- there were five questions and the students chose four.


Introductory matters
====
In general, this covers everything we did up to when we began algorithms, and is the material in Sections 1 and 2 of the notes; unaffected by strike -- we had speed up slightly on this material compared to previous years to try to have more time for later material. 

Questions are almost entirely from the following:
 - Solving or proving insolvability of Instant insanity cubes
 - Proving a graph is or is not (semi)-Eulerian i.e., using and proving Euler's Theorem
 - Proving a graph is or is not (semi)-Hamiltonian (case by case, a few tricks, proof for Peterson graph)
 - Definition of a tree, proving trees have leaves, and that a tree on $$n$$ vertices has $$n-1$$ edges
- Degrees of vertices, the handshaking lemma, and basic applications to chemistry
 - Proving two graphs are or are not isomorphic.



Question 2: Algorithms
====

This is section 3 of the notes, and was the material covered around the strike.  We skipped one topic traditionally covered -- finding longest paths, and applications of this to scheduling problems.  We also skipped some proofs of material in this section, but I don't believe the proofs skipped have typically appeared on exams anyway. Additionally, Prim's algorithm is a new topic that had not appeared in previous years, when only Kruskal's was covered.

Questions are almost entirely from the following:
 - Using Prim's or Kruskal's algorithm for finding the cheapest weight spanning tree; analysing if there is a unique such tree or more than one
 - Using Dijkstra's algorithm for finding shortest paths between points
 - Traveling Salesman problem: statement, nearest neighbor greedy algorithm for upper bound, finding lower bounds for TSP by considering spanning trees
  - Prüfer code: going back and forth from a labelled tree and its code, and how it proves Cayley's Theorem.

The only things here I would ask you to prove work are those for the Travelling Salesman problem, in particular, I will *not* ask you to prove Prim, Kruskal's or Dijkstra's algorithm works.

Graphs on Surfaces
===
This is Section 4 of the notes, and this material was covered after the strike and is unaffected by it -- I was hoping to have slightly more time on it than we did, but we have the same amount that has been spent in past years. 

Questions are almost entirely from the following:
 - Planarity Algorithm for Hamiltonian graphs, in particular proving $$K_{3,3}$$ and $$K_5$$ aren't planar
 - Kuratowski's Theorem characterising planar graphs: stating it, and using and proving the "easy" direction, i.e., that if a $$G$$ has a subgraph $$H$$ that's a subdivision of $$K_{3,3}$$ or $$K_5$$ then $$G$$ isn't planar.
 - Other surfaces: Drawing graphs on the Mobius band and on the torus (in some previous years there have been questions involving the real projective plane $$\mathbb{RP}^2$$ or the Klein bottle; we did *not* cover that this year and it won't be required
 - Euler's Theorem $$v-e+f=2$$ for planar graphs: proving it and using applications of it.  We are doing a slightly different proof of Euler's theorem this year than in previous years.


Colourings
===

This is Section 5 of the notes, and is the material we will cover in the next two weeks.

Questions are almost entirely from the following:
 - Chromatic number of a graph: definition, determining the chromatic number for a particular graph with proof, proving chromatic number is at most the maximum degree plus one, word problem applications
 - Chromatic Index of a graph: definition, determing the chromatic index of a particular graph with proof, word problem applications; stating Vizing's theorem
 - Chromatic Polynomial: definition, deletion-contraction, proving it's a polynomial, recovering chromatic number, number of vertices, number of edges from it.
 - Calculating Chromatic Polynomial of a graph, using: deletion contraction / induction / gluing along a vertex or an edge

