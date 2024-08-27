---
layout: post
title:  "Thoughts in Binary Search"
date:   2024-08-02 22:09:00 +0530
categories: jekyll update
---

_**NB : Open comments, constructive criticisms all are welcome.**_ 

Binary search is used in sorted arrays to solve some problems in `O(log n)` time. 

What if Binary search is used in problems which does not seem to have sorted elements at all? 
What if binary search reduces time complexity of problems not only from linear to logarithmic?

**Problem:**
You are given an array, which represents blooming time of flowers which are planted in a row.
example array : `[7, 7, 7, 7, 13, 11, 12, 7]`
You are given `k`, which is  no of flowers you needed to make a bouquet, and `m`, which is total no of bouquets you needed to make.
You are asked to return min no of days to make `m` bouquets.
Condition : you are allowed to make bouquet using adjacent flowers only.  

**Solution**: 
Brute force : Get maximum and minimum of arrays(max no of days for all to bloom and min no of days to get atleast one flower bloom). The answer days will lie on this search space ( [minDays, maxDays] )

Make a function which takes the array `arr`, a sample day `d`,  sample bouquet size `k` and sample bouquet count `m`. Maintain a variable `cnt`. Go through the array `arr`. If `arr[i] <= d`  increment count, else append count to another vector `v`. At the end, analyse the vector `v` to get no of bouquets we are able to make `m'`. If `m' >= m` return `true`, else return `false`.
(well you could optimise the code by not taking `v`, ik)


So, this function can be used to know whether a day `d` will be our answer or not. 

We've a search space [`minDays`, `maxDays`] and we've to find min `d` where `d` satisfies the stuffs, binary search comes. 

So, The technique binary search might not be evident from the problem statement, It would come handy in the middle of the problems as well.

**Nilesh's Reply** : Binary search depends on monotonic nature of problem you are trying solve. 
For example a monotonic function `F(x)`: 
here `x` is input value, `F(x)` is true if `x` is from prefix of the array and `F(x)` is false when `x`  is from the other part of array.

Try finding median of an array using binary search.

This is from latest Div4 of cf, try using binary search (easy part) - [https://codeforces.com/contest/1999/problem/G1](https://codeforces.com/contest/1999/problem/G1)

For the above problem, binary search can be further improved using ternary search in this -  [https://codeforces.com/contest/1999/problem/G2](https://codeforces.com/contest/1999/problem/G2)

Ternary search Tutorial - [https://cp-algorithms.com/num_methods/ternary_search.html](https://cp-algorithms.com/num_methods/ternary_search.html)

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
