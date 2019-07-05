---
title: Week 8 Tutorial
sidebar: 8
sidebar-title: Week 8
---

---
## Reversing a linked list
---

First, let us look at the problem of reversing a linked list. Discuss, in groups, what your approach to solving this problem would be. 

Come up with an algorithm to do this (Pseudocode is fine here), and also give the worst-case complexity for it.

When you're done, see if you can answer these questions:
- Do you understand your algorithm well enough to implement it?
- What is the worst-case time complexity?
- How much extra space does your algorithm use?
- Can yoimprove your algorithm?

---

Let's look at two approaches to solve this. Here's the first one:
```
* Create a temporary list initially empty
* While head != NULL
      - make a copy of the node at head (head_copy)
      - insert head_copy into temporary list, at head
      - delete head from input list (which will either update the
         head to the next node, or return NULL if list is empty)
* Return new list head
```

and here's the second:
```
* Create a temporary list initially empty
* While head != NULL
     - Find tail of list
     - Remove (unlink) the tail node
     - insert the tail node into the temporary list at the tail
* Return new list head
```

Answer the following:
- What is the complexity of these algorithms?
- How much space is used by each of them?
- Is one of them *always* better?
- If not, why? How could we improve this?

---
## Removing Duplicates
---

Lets do a similar exercise again with a different problem. How would you remove all duplicate nodes from a linked list?

Work in small groups and come up with an algorithm to solve this problem, along with it's worst case complexity.

When you're done, see if you can answer these questions:
- Do you understand your algorithm well enough to implement it?
- What is the worst-case time complexity?
- How much extra space does your algorithm use?
- Can you improve your algorithm?

---

Let's look at one possible way to solve this problem:
```c
p = head
while p != NULL
    q = head->next
    while (q != NULL)
        if (contents of p == contents of q)
            delete(q)
            q = q->next
    p = p->next
```

Answer the following:
- What is this algorithm doing?
- What is the worst-case complexity?
- What assumptions are you making in your answer above?
- Can you think of a way to improve this algorithm?

---
[Slideshow version](slides/)
