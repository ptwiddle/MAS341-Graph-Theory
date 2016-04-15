---
layout: lecture
title: Lecture 14&#58; Kuratowski's theorem; graphs on the torus
comments: True
---

Kuratowski's theorem
---------

Last session we proved that the graphs $$K_{3,3}$$ and $$K_5$$ are not planar.  We now explain a method to prove a general graph is nonplanar.  We begin with some simple observations.


Lemma 1
=====

If $$H$$ is a subgraph of $$G$$, and $$H$$ is not planar, then $$G$$ is not planar.

Proof
====

If we could draw $$G$$ in the plane, it would produce a drawing of $$H$$ in the plane, a contradiction.  $$\square$$

As an immediate corrolary, we see that $$K_n$$ is not planar for $$n\geq 5$$, as all such complete graphs contain $$K_5$$ as a subgraph.


Our method will be a strengthening of this, based on another observation.  Note that as far as drawing goes, drawing an edge is the same as drawing two edges, together incident on a vertex of degree 2 -- they're both just a line; one of them has an extra dot on it:

![Splitting/Joining an edge](../TeXpictures/split.png)

Subdividing the edge $$e$$ into two edges $$e_1$$ and $$e_2$$ by adding a vertex $$v$$ does not change what it would be like to draw the edge.


Definition
======

Two graphs $$G$$ and $$H$$ are homeomorphic if they are connected by a sequence of either splitting an edge into two edges by adding a vertex of degree 2 in the middle, or the inverse operation of this: merging two edges into one by deleting a vertex of degree two.

Example
=====
The following three graphs are homeomorphic:
![Homeomorphic example](../TeXpictures/HomeoExample.png)



Note: Homeomorphic is a word from topology -- homeomorphic graphs give give "the same" topological space.

Lemma 2
=====

If $$G$$ is homeomorphic to $$H$$, then either both $$G$$ and $$H$$ are planar, or neither $$G$$ nor $$H$$ are planar.

Proof
====

If $$G$$ and $$H$$ are homeomorphic, a drawing of one is the same as a drawing of the other, with some "dots" (vertices) in different positions.  $$\square$$

Example
=====
The following graph $$G$$ is nonplanar, since it is obtained from $$K_{3,3}$$ by subdividing a single edge.

![K33 Subdivision](../TeXpictures/K33homeo.png)


Putting together the two lemmas, we see that we can find a

Example: The Petersen graph is not planar
=====

![PetersenSubgraph](../TeXpictures/PetersenNonPlanar.png)

The subgraph drawn with thick edges (containing all but two of the edges in the Petersen graph) is homeorphic to $$K_{3,3}$$.  we have drawn three vertices blue and three vertices red to highlight the vertices of $$K_{3,3}$$.  The nonhighlighted edges are in the subgraph, but they are the ones that are forgetten to show that the highlighted graph is homeomorphic to $$K_{3,3}$$.


Kuratowski's Theorem
========

A graph $$G$$ is nonplanar if and only if it contains a subgraph homeomorphic to $$K_5$$ or $$K_{3,3}$$.

Today's two lemmas, together with yesterday's result that $$K_{3,3}$$ and $$K_5$$ are nonplanar, prove the "if" direction.  The "only if" direction is much harder, and we will not prove it.

However, we will only use the "only if" direction implicitly.  Using the "only if" direction explicitly would amount to prove that some graph was planar by showing it had no subgraphs heomeomorphic to $$K_5$$ or $$K_{3,3}$$, which we would be quite laborious.  We have a much easier way to prove that a graph is planar: drawing it in the plane.

We will however, use the "only if" direction implicitly in the following way.  Suppose we have a graph $$G$$, and we want to determine if $$G$$ is planar or not.  We can try to prove it is planar by trying to draw it in the plane.  We can try to prove it is not planar by finding a subgraph of $$G$$ that is homeomorphic to either $$K_{3,3}$$ or $$K_5$$.  The "only if" direction of Kuratowski's theorem tells us that one or the other of these attempts will *always* work.  Thus, we have a practical method to determine whether or not a graph is planar or not -- try to draw it in the plane.  If you find this difficult, and begin to expect that it isn't possible, start looking for a subgraph homeomorphic to either $$K_5$$ or $$K_{3,3}$$ to prove it.


Graphs on other surfaces
-------------

We now transition to drawing graphs on other surfaces.  In lecture, we had some <a href="http://slides.com/pauljohnson/deck-2#/">slides providing pictures</a> for the beginning of this discussion; a few, but not all, of those images are in the body of these notes now.

Trying to draw graphs on surfaces can be fun, but it seems like a rather unmotivated question to consider, so we began with motivating it by videogames.  Many videogames (pacman, asteroids, overhead RPGs like the early Final Fantasy games) take place on a rectangle screen:

![Videogame map](../Slides/Pictures/chronostatic.gif)

To avoid making the world have an "edge", the result will often happen: if a character moves off the right of the screen it will reappear at the edge of the left screen, and similarly if a character moves off the top of the screen, it reappears on the corresponding place on the bottom of the screen.  

This set-up is used to simulate the surface of a planet.  However, if one traces through the result of these identifications, one sees that the surface is a torus:

![map folding](../Slides/Pictures/chronofolding.gif)





Definition
=====

A "video-game graph" is one that "locally looks like" a part of graph paper.

Question
====

If videogame designers were more clever, could they put a finite videogame graph on the sphere?  Can you prove that it isn't possible?



Drawing graphs on the torus
------

If we wanted to draw a graph on the sphere, we could do this physically by taking a balloon and a felt pen, but it would be a little awkward to turn in or mark homeworks this way ;)  Luckily, we saw last time that, using stereographic projection, drawing a graph on the sphere is equivalent to being able to draw it on the plane.

Similarly, we could draw graphs on torus by getting donuts, and writing on them with icing sugar.  But again, this is rather impractical, and we'd like a way to represent drawing a graph on a torus that is conveniently done on a piece of paper.  

The videogame / paper-folding discussion shows us how to do this.  We draw a square to represent the torus.  On the top and bottom border we draw one arrow in the same direction, to signify that these edges will be identified (this is how the paper was folded, or what a character does in the videogame).  We do similar with the side borders, with two arrows.  

Then we can draw the graph in the square, with the following added options -- if a drawn edge reaches the left (right) border, it continues at the same spot on the right (left) border, and similarly with the top/bottom borders.  


Example
====

$$K_5$$ and $$K_6$$ cannot be drawn on the plane, but they can be drawn on the torus as follows:

![K5 and K6 on the torus](../TeXpictures/K5K6torus.png)

The graph on the left shows $$K_5$$ on the torus.  The picture on the right has the same drawing of $$K_5$$ in black, but in red has added an extra vertex and 5 extra edges incident to it to make a $$K_6$$.  There are appear to be 4 red vertices, at each corner of the square, but since all the corners get identified by the folding, they correspond to the same point of the torus. 


Challenge
=====

Draw $$K_7$$ on the torus.  

It turns out that $$K_8$$ cannot be drawn on the torus; we will prove this later.


What comes next?
-------
what other surfaces other than the sphere and torus are possible?  One possibility is just adding  "more holes"; this produces the "donut with $$g$$ holes", more formally known as the "suface of genus $$g$$".



Are any other surfaces possible?  What is a convenient way for drawing graphs on a $$g$$-holed torus?  We will prove the following theorem: 

Any finite graph $$G$$ can be drawn on a surface of genus $$g$$, for some $$g$$ large enough.





