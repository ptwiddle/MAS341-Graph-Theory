---
layout: bulletin
title: Week 4 Bulletin
comments: True
---
Morning: Trees, Prim and Kruskal
=====

The morning session was cut short by a fire alarm.  We recalled where we were before a strike; defined trees and forests and gave (without proof) many equivalent formulation of what a tree is -- see [here](https://ptwiddle.github.io/MAS341-Graph-Theory-2017/lecturenotes/lecture6.html) for notes stating the result and proofs of some of the equivalences.

We then briefly discussed finding minimal weight spanning trees in weighted graphs.  We described two "greedy algorithms" to do so, Kruskal's algorithm, which always chose the cheapest edge that didn't make a cycle, and Prim's algorithm, which started at one point and always added the cheapest edge you can "see".  Running either algorithm is quite simple, but it is not clear that either algorithm actually finds the cheapest spanning tree; the proof that this is true is one of the casualties of the strike.

(Embarrassing note: in lecture I wrote Prym by mistake, as I'm more familiar with the [19th century algebraic geometer](https://en.wikipedia.org/wiki/Friedrich_Prym) than the [20th century computer scientist](https://en.wikipedia.org/wiki/Robert_C._Prim) )

Afternoon: Leaves, Cayley's theorem proved by Prufer code
=======

In the morning, we claimed without proof that in general graphs can have a huge number of spanning trees, and hence trying to find the cheapest one by enumerating all possibilities is not a good way forward.  In the afternoon, we made this precise, stating Cayley's Theorem that there are $$n^{n-2}$$ labelled trees on $$n$$ vertices (which are the same as spanning trees of the complete graph $$K_n$$).

We proved Cayley's theorem by using the Prufer code; and in order to describe the code we first had to talk about leaves of trees; we showed every finite tree has at least two leaves by considering paths in the tree, and then using induction we proved that a tree with $$n$$ vertices has $$n-1$$ edges.  We then gave another proof that trees have leaves using this fact and the handshaking lemma.

We were then in a position to describe the Prufer code, which iteratively prunes away the leaf with the smallest label.  This gives a bijection between labelled trees on $$n$$ vertices and lists of $$n-2$$ numbers between 1 and $$n$$, proving Cayley's theorem.


