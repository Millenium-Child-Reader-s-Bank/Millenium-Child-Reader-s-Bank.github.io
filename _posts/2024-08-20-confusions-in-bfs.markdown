---
layout: post
title:  "[Past] : When I was confused with BFS"
date:   2024-08-20 22:09:00 +0530
categories: jekyll update
---

I'm always confused about bfs. Okay the concept is pretty simple Ik, we are traversing the nodes of a graph breadth wise from a start node. 
But the thing that confuses me is that should we mark a node visited before pushing it into the queue? or should we mark the node which is dequeued from queue as visited? 

I need a concrete explanation for this. 

**Edit** : _You are encouraged to know Depth First Search Traversal on Graphs before reading further_

We mark node visited before pushing it into queue, so that we can avoid cases where same node could be enqueued multiple times. When it will happen?
 
Lets say we are exploring a graph using bfs, and let us mark a node visited when it is dequeued from queue. Let us assume the node we are currently exploring is `a`. Let node `b` be a child of `a`. According to the procedure of bfs, we enqueue `b` to the queue (here, without marking as visited). Lets say there is another node `c` in the graph and lets say `b` is a kid of `c` . Let say we happened to explore `c`  before dequeueing `b` from the queue. There, we'll see that `b` is a kid of `c`,  and we'll enqueue `b` again.

Comments are welcome(although I think above explanation is sufficient)

**Nilesh's Reply** : _... times. When it will happen?_

consider graph which has 6 nodes `{a, 1, 2, 3, 4 b}`, and total 8 edges, `a` is connected to nodes from 1 to 4, `b` is connected to nodes from 1 to 4, `a` is the root node

start bfs from  root `a`, 
elements in queue will be in order `[a 1 2 3 4 b b b b]` if we mark visited at dequeue
elements in queue will be in order `[a 1 2 3 4 b]` if we mark visited at enqueue

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
