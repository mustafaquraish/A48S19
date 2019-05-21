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


> The math library is one of the most used ones available, with a host of different functions and constants you can use! You should look up what else is available to use, it may be helpful to you when programming in C - there's no need to reinvent the wheel.

