---
title: Week 2 Tutorial
sidebar: 2
sidebar-title: Week 2
---

---

## Working with the C memory model

---

In this exercise, we're going to trace a piece of code and see how all the variables are being stored in the memory model. Before we do this, it is important that you have read the Unit 2 notes - we'll be using the same method as those to do our analysis here.
  
  

> ### Why do we need to do this at all?  
> 
> C is very low level, and understanding what is going on in memory is going to be **crucial** to writing and debugging complex programs effectively. Yes - it's tedious at first, but once you get used to thinking this way, you will find yourself less prone to making a lot of common errors. This also carries over to other programming languages!


Now, here's the code we will be working with today:

```c
#include<stdio.h>
#include<stdlib.h>

int multiply_with_table(int a, int b) {
  // Prints the multiplication table for a starting at 1 and
  // going up to b, returning the value of a*b.
  // e.g.  multiply_with_table(2,5)
  // prints:
  // 2x1=2
  // 2x2=4
  // 2x3=6
  // 2x4=8
  // 2x5=10
  // And returns 10

  int i;
  for (i=1; i<=b; i=i+1) {
    printf("%dx%d=%d\n",a,i,a*i);
  }
  return a*b;
}

int main() {
  int x=5;
  int y=15;
  int z;
  z=multiply_with_table(x,y);
  printf("The result of %x x %d is %d\n",x,y,z);
}
```

Here's questions you should be able to answer **without** running the code:

- How many boxes will be used by this program?
- After any given line of code is run, what boxes have what values stored in them? Which variables do each of these boxes represent?
- When are the boxes for return values in both functions updated and/or used?
- What will be printed after this program is run?

Once you've answered these questions on paper, run the program to see if your answer was correct.

---

## A division program

---

For this exercise, you will be completing the following code according to the comments:

```c
#include<stdio.h>
#include<stdlib.h>

int find_multiplier(int a, int b) {
  // Return an integer c such that  b = a * c
  // If no such integer exists, return -1
  // However, do *NOT* use the division operator.


}

int main() {
  // Declare and initialize two positive integers a and b


  // Call the find_multiplier() function with these and 
  // print out the return value to the screen


  return 0;
}
```

Make sure you get this working! After you're done, ask yourself these questions:

- What are the limitations and assumptions in your solution?
- When do you stop trying different values for `c`?
- Are there different ways to do this? Why are they better / worse?
- Why are you doing it this way anyway?

> The point of this exercise is to illustrate that some problems may not have
    an obviously right/wrong answer. We always want to be thinking critically of the programs
    we write, and trying to understand what's good/bad about the approach we have chosen.

Before we get wrapped up, let's try and think about extending what we just did here.

---

## A harder division problem

---

Having implemeted the above program, you now maybe understand that division isn't a very trivial operation.
However, you've just been working with integers so far. What would happen if you were working with floating point numbers instead? Being able to do this is something we take for granted when programming, but it is definitely not trivial!

Give it some thought - how does the CPU in your computer divide floating point numbers? Could you implement a solution
similar to the exercise above with them? Here's some skeleton for you to work off:

```c
#include<stdio.h>
#include<stdlib.h>

float find_multiplier_floats(float a, float b) {
  // Return a float c such that b = a * c
  // You may assume a is non-zero. This is tricky!


}
```

*Try this!* It may not be easy, but it's great practice in problem solving as well
as coding in C. If you manage to do it, come and show us! We'll be glad to talk to you about it :)

---

# Additional Exercises

---

1. Take the division functions you implemented above and trace the memory model for them. It's good practice for your quiz and exams!

2. Read the notes. They're extremely detailed with a whole bunch of examples and exercises for you to do. Attempt them all!

3. Write a program that loops over the numbers from 1-100, and prints out all the perfect squares. Analyze your solution: Is this an efficient way of doing it? If instead you had to loop over the numbers from 1-900, how much code would you need to change to accomplish this? (Ideally, it shouldn't be more than one line).

---
[Slideshow version](slides/)