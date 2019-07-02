---
title: Week 7 Tutorial
sidebar: 7
sidebar-title: Week 7
---

---
## Exercise 6 Overview
---

First, we're going to discuss exercise 6, since a bunch of people had trouble doing it. Then we'll talk about how to avoid situations like it in the future by talking about testing our code. 

Ask yourselves these questions about the assignment, and see if you can answer them properly:

- What does Forward Euler do?
- How does it work? 
- What does it change every iteration?

The point of the Forward Euler function is to estimate the next position of the squirrel based on it's current position and velocity. Can you see why this is the case?

> Keep in mind that it's **not enough** to *kind of* understand what the function is doing, you need to **completely** understand it.

Now, ask yourself similar questions about the function that finds the optimal velocity.

- What does it do?
- What are some ways to get this to work?
- What is the input, and what gets updated?

It is important to be able to answer all these questions before you begin to attemp a solution to the exercise. In summary:

- You can't solve a problem if you don't understand *exactly* what is being asked of you
- You can't test a program if you don't understand *in detail* what it should be doing at every step
- Don't make assumptions that you don't need to! If you don't understand something, feel free to look it up instead of assuming what you think might be the correct answer.
- Wikipedia is a wonderful resource, so is Google.

---
## Testing
---

Programs (at least written in C!) do not behave randomly or develop weird behaviour. They do as they are told, *every time*. If the program is not doing what it should - it has a bug that you need to fix. For this, you need to know what the program should be doing at each step. (This isn't optional). Now, here's the question:

<center><h3>How do you test your code?</h3></center>

- First, you need to understand what your code is doing.
- Second, you need to come up with test cases *on paper*.
- If you're given any tests, look at them to see what's going on
- Use a debugger if you need to! (Also look [here](../debug))