---
layout: lecture
title: Lecture 4&#58; Proofs of Lemmas; Eulerian cycles
comments: True
---




Lemmas on walks
-----


Lemma
===

The following are equivalent:

1. $$\Gamma$$ is connected.
2. There is a walk between any two vertices $$v, w\in V(\Gamma)$$

Proof
===

1 implies 2: Supppose that $$\Gamma$$ is connected, and let $$v, w\in V(\Gamma)$$; we want to show that there is a walk from $$v$$ to $$w$$. 

Define $$S\subset V(\Gamma)$$ to be the set of all vertices $$u\in V(\Gamma)$$ so that there is a walk from $$v$$ to $$u$$; we want to show that $$w\in S$$.

First, observe that there are no edges from $$S$$ to $$V(\Gamma)\setminus S$$.  Suppose that $$e$$ was an edge between $$a\in S$$ and $$b\in\Gamma\setminus S$$.  Since $$a\in S$$, by the definition of $$S$$ there is a walk $$v=v_0v_1v_2\cdots v_m=a$$ from $$v$$ to $$a$$.  We can add the edge $$e$$ to the end of the walk, to get a walk from $$v$$ to $$b$$, and hence by definition $$b\in S$$.  

Now suppose that $$w\notin S$$.  Then $$S$$ and $$V(\Gamma)\setminus S$$ are both nonempty, and by the above there are no edges between them, and so $$\Gamma$$ is not connected, a contradiction.

To prove 2 implies 1, we prove the contrapositive.  If $$\Gamma$$ is not connected, then there are two vertices $$v,w\in V(\Gamma)$$ so that there is no walk from $$v$$ to $$w$$. 

Suppose that $$\Gamma=\Gamma_1\sqcup\Gamma_2$$, and pick $$v\in V(\Gamma_1), w\in V(\Gamma_2)$$.  Any walk from $$v$$ to $$w$$ starts in $$V(\Gamma_1)$$ and ends in $$V(\Gamma_2)$$, and so at some point there must be an edge from a vertex in $$\Gamma_1$$ to a vertex in $$\Gamma_2$$, but there are no such edges $$\square$$

Lemma
===
A graph $$\Gamma$$ has a closed odd length path if and only if it has a closed walk of odd length.

Proof
====

A closed path of odd length is obviously a closed walk of odd length, so one implication is trivial.

Now, suppose $$v_0v_1\dots v_m=v_0$$ is a closed walk of odd length, but not a path.  Then some vertex is repeated; say, $$v_i=v_k$$, with $$i<k$$.  Then we may "pinch" the original closed walk into two smaller closed walks: $$v_0v_1\dots v_i v_{k+1}\dots v_m=v_0$$ and $$v_iv_{i+1}\dots v_k=v_{i+k}$$.  If these walks of lengths $$\ell_1$$ and $$\ell_2$$, then $$\ell_1+\ell_2=m$$, and since $$m$$ is odd one of the $$\ell_i$$ has to be odd, and we have have fund an odd walk of strictly shorter length.  Continuing this, we must eventually find an odd length walk with no vertices repeated.  $$\square$$


Lemma
===
A graph is bipartite if and only if it does not have an odd cycle.




Proof
===

Since the odd cycle is not bipartite, any graph containing an odd cycle cannot be partite; the harder direction is to show that if $$\Gamma$$ does not have an odd cycle, then it is bipartite.  

The proof proceeds by trying to color the vertices of $$\Gamma$$.  Pick any vertex $$v$$, and define $$S_k$$ to be the set of all vertices with distance exactly $$k$$ from $$v$$.  We will try to color $$\Gamma$$ by coloring the vertices in $$S_n$$ to be red if $$n$$ is even, and blue if $$n$$ is odd.  

Suppose that this is not a valid coloring; then we have a vertex $$a\in S_k$$ with $$k$$ even, adjacent to a vertex $$b\in S_\ell$$ with $$\ell$$ odd.

Since $$a\in S_k$$, there is a path $$v=v_0v_1\cdots v_k=a$$; and similarly since $$b\in S_\ell$$ there is a path $$v=w_0w_1\cdots w_\ell=b$$.  Concatening these gives us a closed walk $$a=v_kv_{k-1}\cdots v_0 w_1 w_2\cdots w_\ell=b$$ of length $$a+b$$ which is odd; since $$a$$ and $$b$$ are adjacent this gives us an odd walk in $$\Gamma$$, and hence by the previous lemma an odd path $$\square$$.


Eulerian and Hamiltonian cycles
-----

Since trails are not allowed to repeat edges, and paths aren't allowed to repeat vertices, the biggest they can get in a finite graph $$\Gamma$$ is to visit every edge, respectively vertex, once.  

Definition
====
 - An *Eulerian* cycle is a closed walk in $$\Gamma$$ that visits every edge exactly once 
 - A *Hamilton* cycle is a closed walk in $$\Gamma$$ that visits every vertex of $$\Gamma$$ exactly once.

It is very natural to ask whether a given graph $$\Gamma$$ has an Eulerian/Hamiltonian cycle.  Though these questions seem very similar, their difficulty is very different: we shall quickly see that it is very easy to tell if a given graph has an Eulerian cycle, but it turns out it is hard to tell if a given graph has a Hamiltonian cycle.


Bridges of Konigsburg
----

Eulerian cycles are so named because of the following story: the city of Konigsburg (now Kaliningrad) was built on both sides of a river, and contained two large islands.  The 4 sectors of the city were connected by seven bridges, as follows:



The question arose whether one could take a walk in the city, crossing every bridge exactly once, and return to where one started.  We can translate the question into graph theory: the four land-masses are vertices, and the bridges are edges.  The question then reduces to whether graph has an Eulerian cycle.  

Euler proved that no such stroll around Konigburg existed, by proving the following more general result.

Lemma
===
If a graph has a verex with odd degree, then it does not have an Eulerian cycle.

Proof
===

Suppose that $$v\in V(\Gamma)$$ has an odd degree, and consider a closed path in $$\Gamma$$.  The path may visit $$v$$ multiple times; each time it does, it must enter from one edge, and leave from another edge, unless we leave along a loop, and return via the loop).  In either case, each time the path visits $$v$$, it "uses up" two of the degree of $$v$$.  Therefore, if $$v$$ has odd degree,  for any closed path there will be an edge incident to $$v$$ that wasn't used in our path, and hence the path will not be Eulerian.  $$\square$$

The above lemma shows that a necessary condition for having an Eulerian cycle is that every vertex has even degree.  Another obvious necessary condition is that the graph is connected.  It turns out that these two conditions are also sufficient.  In the next lecture, we will prove the following:

Lemma
===

If $$\Gamma$$ is connected, and every vertex has even degree, then it has an Eulerian cycle.



