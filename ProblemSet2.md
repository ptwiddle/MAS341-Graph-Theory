---
layout: default
permalink: /ProblemSet2/
---

Problem Set 2
----


This problem set does not contribute to your final course grade, but is useful practice writing proofs for the exam.  It is due in class on Friday, March 31st. 


Question 1
---

The triangular prism graph is the graph with 6 vertices and 9 edges shown below:
Find a Hamiltonian cycle in the following graph:
![Triangular Prism](../triangularprism.png)

As of this writing (hopefully one of you will fix it; I've never edited wikipedia), the [Wikipedia article for prism graphs](https://en.wikipedia.org/wiki/Prism_graph) has a mistake in the formula for the number of spanning trees (if you follow the link to their source, they just miscopied something).  

Prove that, in fact, the triangular prism graph has 75 spanning trees, not 78.  (One possible way to organize the count: consider the three edges NOT contained in any triangles.  There are 12 spanning trees that contain all three of these, 36 spanning trees that contain 2 of these edges, and 27 spanning trees that contain just one of these edges).


Question 2
---
Prove that the number $$k$$ appears $$m$$ times in the Prufer code for a tree $$T$$ if and only if the vertex labelled $$k$$ in $$T$$ has degree $$m+1$$.

Show that this implies that the number of trees on $$n$$ labeled vertices, where vertex $$i$$ had degree $$d_i$$, is the multinomial coefficient

$$\binom{n-2}{d_1-1, d_2-1,d_3-1,\dots, d_n-1}=\frac{(n-2)!}{(d_1-1)!(d_2-1)!\cdots (d_n-1)!}$$ 


