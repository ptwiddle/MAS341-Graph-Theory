---
layout: lecture
title: Lecture 5&#58; Algorithms and Proofs; Existence of Eulerian cycles
comments: True
---

Algorithms and Proofs:
-----

An *algorithm* is just a step by step recipe for finding or calculating something; a *proof* is a logical justification of why something is true; it's worth a few minutes to discuss how these are related.

Often, we want to prove something exists -- for instance, a path between two vertices, or an Eulerian cycle.  One obvious way to do this is to actually construct the object; usually, this amounts to giving an algorithm for making it, and a proof that the algorithm always works.  In any case, constructive proofs can usually be rewritten to produce an algorithm.

However, there are also *nonconstructive proofs*, where we prove that an object exists but dont' give any indication of how to actually find it.  One common way non-constructive proofs occur is in proofs by contradiction.  For example, in the last lecture we proved that if a graph $$\Gamma$$ is connected, then there is a path between any two vertices in $$\Gamma$$, but we did not find the path; we proved that it exists by contradiction.  

On the other hand, it is important to note that an algorithm is not itself a proof.  An algorithm is just a sequence of steps -- to turn it into a proof, it is necessary to justify that the sequence of steps will always produce the desired outcome.  

Back to Eulerian cycles
-----

We ended the last lecture by stating the following Lemma:



Lemma
===

If $$\Gamma$$ is connected, and every vertex has even degree, then it has an Eulerian cycle.

We will now prove this Lemma; first, we will give an algorithm for finding Eulerian cycles in a graph, and demonstrate it in an example.  We will then rigorously prove that, if $$\Gamma$$ is connected and every vertex has even degree, that the algorithm will always actually find an Eulerian cycle.

The algorithm
===

The algorithm will run inductively by taking a closed walk $$w$$ that does not repeat any edges, and if it does not use every edge of $$\Gamma$$ it will increase it to a walk $$w^\prime$$ that contains all the edges of $$w$$ together with some new edges.  We can initial the starting walk to be a constant walk at any vertex $$v$$.  Since $$\Gamma$$ has only a finite number of edges, after a finite number of iterations we see this algorithm will produce an Eulerian walk.

Intuitively, in the language of cross bridges, the algorithm is the following: thinking back on the closed walk you did, find a bridge that you saw but never crossed over.  Start a new walk from that bridge, taking only bridges you never crossed, until you get back to where the new walk started.  Then join these two walks together into a longer one.

More formally, the algorithm is as follows:


1. Find an edge $$e$$ that is not contained in $$w$$, but shares a vertex with $$w$$.  Say, $$e$$ is between $$u$$ and $$v$$, with $$u\in w$$.
2. Start building a walk $$Q$$ of unused edges from the *other* vertex of $$e$$ -- that is, find an edge $$f$$ adjacent to $$v$$, so that $$f$$ is not in $$Q$$ or $$w$$.
3. Continue extending $$Q$$ by unused edges until we return to the starting vertex $$u$$ of $$Q$$, making a closed walk.
4. Merge the two closed walks $$w$$ and $$Q$$ to make a longer closed walk.







Proof
===

Let $$P$$ be a closed walk in $$\Gamma$$ -- as a base case, we can take $$P$$ to be the empty walk that just stays at $$v$$.  We inductively show that if $$P$$ does not use all the edges of $$\Gamma$$, then we can enlarge $$P$$ to a longer closed walk, which would complete the proof.

Suppose that there is some edge $$e$$ that is not in $$P$$.  We first show that there is some edge $$f\notin P$$ that contains a vertex that is in $$P$$.  
If one of the vertices of $$e$$ is in $$P$$, we can just take $$f=e$$.  If not, then consider any vertex $$v\in P$$, and a vertex $$w$$ incident to $$e$$.  Since the graph $$\Gamma$$ is connected there is a path $$Q$$ from $$v$$ to $$w$$.  Since $$w\notin P$$, eventually the path $$Q$$ must contain an edge not in $$P$$ -- we can take $$f$$ to be the first such edge.

So, now, we have a vertex $$v\in P$$, incident to an edge $$e\notin P$$.  We claim we can grow $$e$$ into another closed trail $$Q$$, that does not share any edges with $$P$$.  



Let $$v_1$$ be the other end of the edge $$e$$; if $$v_1=v$$, we are done.  If not, then consider the edges incident to $$v_1$$ that are used in $$P$$ and our new path $$Q$$: there are an odd number, but $$v_1$$ has an even degree, and so there must be another edge incident to $$v_1$$ that is not in $$P$$ or $$Q$$, and so we can extend our trail.  Continuing this process, our trail must eventually reach $$v_1$$ again, in which case we may stitch together the two trails by first doing $$P$$ starting at $$v_1$$, and then doing $$Q$$ from $$v_1$$ to $$v_1$$.  $$\square$$

Note that this proof not only completely characterizes the graphs that have Eulerian cycles, it provides an algorithm for finding an Eulerian cycle in such a graph.

