---
layout: lecture
title: Lecture 8&#58; Prüfer code	
comments: True
---


In this lecture, we will prove Cayley's formula, using the Prüfer code.  In particular, we will give a map $$PC$$ that takes in a labelled tree with $$n$$ vertices, and returns a string of $$n-2$$ numbers, each between $$1$$ and $$n$$, and an inverse map $$\mathbf{Tree}$$ that takes in a string of numbers and returns a labelled tree.  

The starting observation is that to write down a labelled tree is the same as writing down its $$n-1$$ edges.  Since the vertices are ordered, each edge can be written down by a pair of numbers in $$\{1,\dots,n \}$$. The Prüfer code begins by writing down these edges in a clever ordering.  


The Prüfer code
----

We are now ready to introduce the Prüfer code.  We begin by writing down the edges of $$T$$.  The two vertices of each edge will be written down in a column, with the parent vertex in the top row and the child vertex on the bottom row.  We record the edges in the following specific order.

 First, find the lowest numbered leaf, and record its number in the bottom row.   Above it, write down the number of the vertex this leaf is adjacent to, which we call the parent vertex.  Now, delete that lowest numbered leaf and the edge connecting it to the rest of the tree.  Find the lowest leaf on the resulting vertex, and record its number, and the number of its parent, in the next column.  

Iterate this procedure until we have written down all $$n-1$$ edges of our tree, with the leaf numbers in the top row, and the parent numbers in the bottom row.

The list of the first $$n-2$$ parent numbers (i.e., all but the last), is the Prüfer code of $$T$$.

Example
===

We illustrate the construction of the Prüfer code by finding the code for the following labelled tree:

<a href="http://www.presheaf.com/?d=d1483r4h5s5l12l4i4g1d2w2z292r34"><img src="http://presheaf.com/cache/d1483r4h5s5l12l4i4g1d2w2z292r34.png" title="click to go to presheaf.com for editing"/></a>

The lowest leaf is 3, which is attached to 1, so the first column goes

<table>
<tr>
   <td> Parent node </td>
   <td> 1</td>
   <td> 6</td>
   <td> 6</td>
   <td> 2</td>
   <td> 2</td>
   <td> 7</td>
</tr>
<tr>
  <td> Child node </td>
   <td> 3</td>
   <td> 1</td>
   <td> 4</td>
   <td> 5</td>
   <td> 6</td>
   <td> 2</td>   
</tr>
</table>

Thus, the Prüfer code for the above tree is 16622.

Reconstructing a tree from its Prüfer Code
===

It is clear from the above definition that the Prüfer code is a list of $$n-2$$ numbers between 1 and $$n$$; it is not clear that any such list of numbers is obtained, nor that any two trees give us a different set of numbers.  To see this, we describe an inverse algorithm, that constructs a tree on $$n$$ vertices from a Prüfer code.  

More explicitly, the inverse algorithm will take as input a Prüfer code, and from that Prüfer code it will reconstruct the full ordered table of edges we constructed in the Prüfer code algorithm.  It should be clear from the description that the algorithm actually reproduces this table, and not some other table, and hence that the two algorithms are inverse to each other.  This shows that the Prüfer code is a bijection, which proves Cayley's formula, as there are $$n^{n-2}$$ valid Prüfer codes on $$n$$ vertices.

This algorith proceeds by figuring out the corresponding child nodes one by one.  Recall that any number in our list appeared as a parent node, and so is not a leaf.  At the first step, we deleted the smallest leaf.  So the first child node is the smallest number that does not appear on our list.  

After we recorded that edge, we deleted it; thus, the second child number is the smallest number that we haven't 

1. already used as a leaf number   
2. doesn't appear at or after the current spot as a parent.

Example
===

We first reconstruct the tree we did in the first example, from its code.
Recall, the Prüfer code was 1 6 6 2 2.

The lowest unused number is 3, so that is the first child.

To find the next unused number, we move to the second column.  1 only appears in the first column, and so it is now the lowest number that doesn't appear, and so it goes underneath the first 6.  Moving to the third column, we have already used 1 and 3 as child nodes.  The number 2 is still to appear as a parent, and so can't be a leaf yet, and so 4 is the first number that we haven't used yet.  Similar reasoning gives 5 and 7 for the 4th and 5th column.  

Finally, the last remaining edge connects the two nodes we have not used as leaves yet; in this case 2 and 6.  


Number of trees with a given degree sequence
------

The Prüfer code actually proves a stronger statement: it counts the number of labelled trees where vertex $$i$$ has degree $$d_i$$.  More specifically:

Corollary
======
The number of labelled trees on $$n$$ vertices where vertex $$i$$ has degree $$d_i$$ is

$$\left( \begin{array}{cc} n-2 \\ d_1-1,d_2-1,\dots, d_n-1 \end{array}\right)=\frac{(n-2)!}{(d_1-1)!(d_2-1)!\cdots (d_n-1)!}$$

Proof
=====

First, observe that vertex $$i$$ of a labeled tree $$T$$ has degree $$d_i$$ if and only if $$i$$ appears $$d_i-1$$ times in the Prüfer code $$PC(T)$$.  This can be seen by building the Prüfer code: each time $$i$$ occurs in the Prüfer code we delete an edge incident to $$i$$, and finally $$i$$ will occur a final time as a leaf.  

Then, the number of labeled trees we want to count is the number of sequences of $$n-2$$ numbers, where $$i$$ occurs $$d_i-1$$ times, which is counted by the given multinomial coefficient.




