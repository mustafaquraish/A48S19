---
title: Week 11 Tutorial
sidebar: 11
sidebar-title: Week 11
---

---

## Simple Graphs

---

The purpose of the tutorial this week is to work with some simple Graphs. First, let's form a little graph, and come up with an adjacency list and an adjacency matrix representation for it.

Here's how we will form the graph:
- Number each person from 1 to N.
- Draw a node for each person on the board, with their # and name in it
- Draw an edge between 2 nodes if they are friends with each other

This is an example of a simple social graph! There's a bunch of interesting questions you can ask using these, and if you end up taking CSCC46 (Social and Informational Networks), you'll do a lot of cool analysis on these! For now, let's focus on a (relatively) simple question:

> Is there a chain of people connecting a person A to another person B?

Before we do that - let's first build up our adjacency matrix to use. Remember that this is an undirected graph, so the diagonal of the matrix should be 0. Also bouble check that everything is ok with your graph by checking that it is symmetric. This trick works since if person A knows person B then person B knows person A.

---
## Depth First Search (DFS)
---

This is the first algorithm we'll look at to answer our question above. First, pick two points A and B you want to find a path (or chain of friends) between.

Now, using the DFS pseudocode from the lecture notes, see if you canperform DFS on our graph to find the result. Here are some things to keep in mind:

- You don't always get there on the first try - maybe you reached a dead-end and had to backtrack
- You may not get the same order as someone else, it's likely that they went in a different order than you did. There's lots of right answers here!

If you got a different answer from someone else, ask around to see what they did differently! The order in which you visit your neighbours here matters.

---
## Breadth First Search (BFS)
---

BFS is another algorithm that allows us to find the *shortest* path between two nodes in an unweighted graph. The general idea for BFS is as follows:
 - If you're not the target, you ask *all* your (unasked) neighbours if they know the target.
 - Any person who was asked first, gets a chance to ask their neighbours first.

The second point is important here. Since DFS does not have this restriction, and you can keep following a chain arbitrarily till you reach the goal or a dead end. That is not the case here. 

Using the idea above, see if you can run BFS on the graph, or some up with some pseudocode on how you would actually implement this. Keep in mind:
- BFS gets you the shortest length of path possible
- Your BFS program may not neccessarily be as efficient as your DFS, it depends on the graph

---

Now that you've finished running BFS, let's see if we can formalize it into an algorithm. Remember the important point we talked about above? In order to run the algorithm in that way, we need a data structure called a **Queue**. 

What is a Queue? It's a data structure with an `add()` and `pop()` function - except with the important caveat that you can only pop (remove) the element in the Queue that was added the earliest. (So, if I add `G`, `A`, `H`, `K` in that order, calling `pop()` multiple times will return them in the same order). You can choose to implement this however you like (linked lists, arrays, etc) as long as it has the required functionality.

With that out of the way, here's the pseudocode for BFS. This is the iterative approach, however it can also be done recursively.

```
- Add start node to the queue and mark it visited
- While queue is not empty:
-    pop node from queue, and mark it visited
-    if the current node is the destination, exit loop
-    Add all unvisited neighbours to the queue
- If the loop was exited at the destination, there is a path
- else there isn't a path
```

Now - this is not quite done yet. This algorithm is not quite done yet - this only tells us that a path exists, but doesn't tell us what the actual shortest path is. For that, we're going to need to modify the function a little.

The details of implementation will be left up to you - but here's the general idea of what you need to do:
- Keep track of which neighbour added every node to the queue (except the start node, ofcourse). Call this the 'predecessor' of a node. This is because if the path goes through this node, then the previous node in the path must have been this predecessor.
- If you reach the destination, then you build up the path by looking up the predecessors till you reach the start node. Our path would then be `A -> ... -> pred(pred(B)) -> pred(B) -> B`.

---

What do you think is the complexity of these algorithms?

---
# Additional Exercises
---

1. Implement a Queue data structure! This should be fairly trivial with that you already know, and will be useful in your A3.

2. Using the pseudocode above, write down code that performs BFS given an adjacency matrix as well as an adjacency list.

3. Also implement the mechanism which helps us get the actual path.

4. Define the distance of two nodes to be the length of the shortest path between them. Write an algorithm that gives you the average distance between any two nodes in a graph represented by an Adjacency matrix. What is it's complexity?

5. (Extra Crunchy!) If you were instead given a weighted graph, could you find the path between two nodes where the sum of weights of the edges along the path is minimized?