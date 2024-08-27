---
layout: post
title:  "A Cyclic Array Problem"
date:   2024-08-25 00:00:00 +0530
categories: jekyll update
---
_Comments, Constructive criticism, opinions and Bug raises are welcome, but guidances are unwelcome_

**Problem** : You are given a cyclic array `a` of size `n`. If any two adjacent elements `a[i]` and `a[i+1]` follow the relation `a[i] <= a[i+1]`, then you can delete any one of them. Find minimum number of deletions so that all elements in cyclic array `a` are equal

**First Intuition** : Elements with maximum number of occurance will stay back.

Of course, an intuition comes to our mind without proof. We want a proof model. For that I had a thought process, which is written below : 

**Proof model** : Let your brain start using your imagination! 
Imagine a polar coordinate system. The coordinates of circular grid are (r, theta). Plot the values of circular array in this grid in such a way that r is the value, and theta is e^{i . pi / n} where i is index. Find a circle where maximum number of plotted points occur. There can be plotted points that appear outside as well as inside the circle. Now construct a polygon by joining adjacent plotted points(which is, in another way, adjacent values in the cyclic array). You can delete any node that appears on an ascending edge or a flat edge.

**The greatest flaw in the plan** : Consider 5-6 adjacent nodes in such a way that the edges connecting them appear like a continuous descending slope. You simply cannot delete the nodes that appear strictly inside this descending slope since the edges donot satisfy the condition for deletion. Right?

**I got the solution** : 
Let `x` be the number which have most number of occurance in the array. So, I have to see whether it is possible to remove all other elements. 

**1**. Consider the elements which are just after `x` whose value is larger than `x`. We can delete them.
**2.** Consider the elements which are just before `x` whose value is not larger than `x`. We can delete them too. 

Repeat 1 and 2 till there is no change in the circular array.  You can prove that this array indeed only contains `x`s, by Proof By Contradiction method. 

So, why the flaw in the plan was not at all a flaw? 
If you think recursively, in the great decreasing slope, there are endpoints. They can be eliminated(I am not that good to explain how in simple words. A future me might edit this line), and the decreasing slope's size decreases. Apply this process multiple times to that slope, so that you could eliminate/*do-whatever-with* the slope

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
