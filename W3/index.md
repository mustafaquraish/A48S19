---
title: Week 3 Tutorial
sidebar: 3
sidebar-title: Week 3
---

---

## Working with Arrays

---

In this exercise, we will write a program that takes in an array of numbers, and then computes the sine and cosine of these numbers using the `sin()` and `cos()` functions of the math library.

Using only *array notation* (no pointers for now), complete the following code according to the given comments:

```c
#include<stdio.h>
#include<math.h>    // This imports the functions from the math library

// Complete the function prototype. What are the parameters needed?
void computeSineCosine( ... parameters ... ) {
  // Complete this function according to the specification
  // given below!


}

int main() {
  // Declare an array 'array' with 10 floating point numbers


  // Fill this array with numbers such that
  //      array[i] = (2 * pi * i) / 10


  // Declare 2 arrays 'sin_theta' and 'cos_theta', both having
  // 10 floating point numbers each.


  // Call the computeSineCosine() function which computes the
  // sine and cosine of all the numbers in 'array' and stores
  // them in 'sine_theta' and 'cos_theta'


  // Print out the sine and cosine for all the numbers!
  // Eg: sin(0) = 0, cos(0) = 1


  return 0;
}

```

After you're done with this, draw out the memory model on a piece of paper and trace the code to make sure you really understand how this works in memory. You should know how your function is getting access to the arrays, and how the computed values are being stored.

> ### This is important!
>
> Understanding how arrays work properly is going to be something that will be useful to you for the rest of your programming career in C, and help you avoid a lot of common mistakes.

Make sure you run your code when you're done to check if it's working correctly!

---
## Using pointers!
---

Now, do the same exercise as above, except using pointers instead of array notation. (Your function will now take in pointers).

Remember this pointer notation:
- Getting the address of something is done by using the `&` operator, as in `&array[5]` gets the address of the 6<sup>th</sup> entry in `array`.
- Accessing information using a pointer is done with the `*` operator, as in `*(p)` is accessing the location whose address is in `p`.
- We can replace `(p)` with expressions that modify the address, like `*(p+3)` gets the location whose address is whatever is in `p + 3`

Once you're done with this, make sure you can answer the following questions:
- How would these programs be different if you traced the memory model?
- What's the difference between using pointers vs. using arrays?
- In this case, or in general, should you be using pointers or arrays? Why?

---
### Some technical issues

- The `sin()` and `cos()` functions are part of the math library, which are not available to you by default. You need to include the library using `#include<math.h>` to be able to use them.

- When compiling your code with the math library included, you need to add the `-lm` flag. This tells the compiler to **l**ink the **m**ath library, which means it will find and include it when compiling your program. For example, instead of `gcc file.c`, we would now compile with `gcc file.c -lm`. Without this, you may get an error.


> The math library is one of the most used ones available, with a host of different functions and constants you can use! You should look up what else is available to use, it may be helpful to you when programming in C - There's no need to reinvent the wheel.


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