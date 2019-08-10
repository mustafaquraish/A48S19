---
title: Week 11 Tutorial
sidebar: 11
sidebar-title: Week 11
---

---
## Simple Graphs
---

First, let's work out a little graph, and come up with an adjacency list and an adjacency matrix for it.

The graph is simple:
- Number each person from 1 to N.
- Draw a node for each person on the board, with their # and name in it
- Now draw an edge to anyone else you who is in the tutorial

It's a simple social graph.

---

Now build an adjacency matrix and list for the graph.

This is an undirected graph, so the diagonal of the matrix should be 0.
Double check that everything is ok with your graph by checking that it is symmetric. This trick works since if person A knows person B then person B knows person A.

---
##Trying out BFS and DFS
---

Pick two points in your graph and use DFS to get from one point to the other. Here are some things to keep in mind:
- you don't always get there on the first try, maybe you reached a dead end and had to backtrack
- you may not get the same order as someone else, it's likely that they went in a different order than you did. There's lots of right answers here!

Now try out BFS on your graph:
- BFS gets you the shortest length of path possible
- your BFS program may not neccessarily be as efficient as your DFS, it depends on the graph

Below is pseudocode for BFS:

```
* When called,
	- mark the current node as visited
	- if the node is the destination, return
	- otherwise, add al the neighbours to a queue (at the tail)
	- call recursively with the next entry in the queue
```

Think about the order that the nodes will be expanded in for a BFS search.
What is the complexity of these programs?

---
[Slideshow version](slides/)
