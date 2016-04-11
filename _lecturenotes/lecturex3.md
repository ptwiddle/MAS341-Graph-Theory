---
layout: lecture
title: Lecture 13&#58; Planar Graphs
comments: True
---

An Old Chestnut
====

Alice, Bob and Carol, are building houses near each other, and each want to connect themselves to the power plant, the sewer plant, and the gas plant by independent underground lines.  Is it possible to do it so that none of these lines cross over each other?





We have typically viewed graphs as drawings in the plane, with the vertices as dots and the edges as lines between them.  Different choices of drawings of them same graph can look very different (as we saw with the Petersen graph).   One thing that is convenient is to have drawings where the edges never cross (we might wonder if the crossing is a vertex).  We are naturally then led to the following definition:


Definition
====

A graph is *planar* if it can be drawn in the plane ($$\mathbb{R}^2$$) so that none of the edges cross.





An interpretation:
===

We can interpret this question in terms of graph theory.  We interpret the places as vertices, and the line between them as edges.  We have two different types of vertices -- the houses (ABC), and the service providers (electricity, water, gas), and the edges only connect one type of vertex to the other, and so we see the graph we are looking at is bipartite.  Furthermore, we want to connect every vertex of one type to every vertex of the other, and so we are working with the complete bipartite graph $$K_{3,3}$$.  

We want to draw this graph in the plane so that none of the lines cross -- which is exactly asking if $$K_{3,3}$$ is planar.


Today's main goal
-----

Our main goal today is to prove that $$K_{3,3}$$ and $$K_5$$ are *not* planar, in particular, giving a negative solution to the old chestnut.

Main idea of the proof
===

The proofs will feel very similar, because they both hinge on the following common feature of $$K_{3,3}$$ and $$K_5$$ -- they are Hamiltonian.  If a graph $$\Gamma$$ is Hamiltonian, and we pick a Hamiltonian cycle through it, then in any drawing of that graph the Hamiltonian cycle will form a circle.  Then, using the deep fact that any circle on the plane has an inside and an outside (the Jordan curve theorem).  Any extra edges on the graph must lie entirely on the inside of the circle or the outside of the circle.  Doing a case by case analysis of these extra edges leads to a proof.

The same idea can be extended to determine whether any Hamiltonian graph is planar or not.




Proof that $$K_{3,3}$$ isn't Hamiltonian
====

Let the vertices $$a,b,c$$ be coloured red and vertices $$x,y,z$$ be coloured blue.  The path $$a-x-b-y-c-z-a$$ is a Hamiltonian cycle, that we draw as a circle in the plane, as shown below:

<a href="http://presheaf.com/?d=d1f3c3z5i342j3s47402p5e1l6h1k2f2i"><img src="http://presheaf.com/cache/d1f3c3z5i342j3s47402p5e1l6h1k2f2i.png" title="click to go to presheaf.com for editing"/></a>

This contains 6 of the 9 edges of $$K_{3,3}$$; we need to add the edges $$a-y, b-z$$ and $$c-x$$.  The edge $$a-y$$ could be drawn inside the circle or outside, suppose we draw it inside, as shown below, with the added edge dashed.

<a href="http://presheaf.com/?d=d6p443t5v3w101e1r2g1u1x156y6870"><img src="http://presheaf.com/cache/d6p443t5v3w101e1r2g1u1x156y6870.png" title="click to go to presheaf.com for editing"/></a>

Then on the inside of the circle, $$x$$ and $$c$$ are on different sides of the line $$a-x$$, and so the edge connecting them must go outside the circle.  The added edge could go around the right of the circle, as shown below here:

<a href="http://presheaf.com/?d=d2s4y614j59131z1j4ul375e2s1r6l4g"><img src="http://presheaf.com/cache/d2s4y614j59131z1j4ul375e2s1r6l4g.png" title="click to go to presheaf.com for editing"/></a>


or around the left, as shown here:

<a href="http://presheaf.com/?d=d4i6r67d2b5z2u3p6ao1g42453q176z"><img src="http://presheaf.com/cache/d4i6r67d2b5z2u3p6ao1g42453q176z.png" title="click to go to presheaf.com for editing"/></a>


But now $$b$$ and $$z$$ are different sides of $$a-y$$ inside the circle, and on different sides of $$c-x$$ outside the circle, and so cannot be connected without making two edges cross.

If we had began by drawing $$a-y$$ outside the circle, then we would have had to draw $$c-x$$ inside the circle, and had the same problem with being able to draw the last line; as shown here:

<a href="http://presheaf.com/?d=d1015p1r712k18714i5l9282s1n621d"><img src="http://presheaf.com/cache/d1015p1r712k18714i5l9282s1n621d.png" title="click to go to presheaf.com for editing"/></a>


Proof that $$K_5$$ isn't planar
====

The proof is similar, in that we begin by picking a Hamiltonian cycle, say, $$a-b-c-d-e-a$$, and drawing this as a cirlce in the plane, and then try to add the remaining edges.  $$K_5$$ has $$5\cdot 4/2=10$$ edges, and 5 are contained in the cycle, so we have 5 more edges to add -- $$a-c, a-d, b-d,b-e$$ and $$c-e$$.

Begin by considering the case that $$a-c$$ is draw *inside* the circle, giving us the following picture:

  


  Then $$b$$ is separated from $$d$$ and $$e$$ on the inside of the circle, and hence the edges $$b-e$$ and $$b-d$$ must be drawn on the outside of the circle.  These edges separate $$a$$ from $$d$$ on the outside of the circle, and so this must be drawn inside, giving the following picture:

<a href="http://presheaf.com/?d=d5f4c451j4lgx3zy171b161j6f52i"><img src="http://presheaf.com/cache/d5f4c451j4lgx3zy171b161j6f52i.png" title="click to go to presheaf.com for editing"/></a>

 but now we cannot add the final $$c-e$$, as $$c$$ and $$e$$ are separated from each other on both the outside and the inside of the circle.

Similarly, if we had drawn $$a-c$$ outside the circle, then $$b-d$$ and $$b-e$$ would ahve had to be drawn inside the circle, and then $$a-d$$ must also be outside, and drawing $$c-e$$ is not possible.




