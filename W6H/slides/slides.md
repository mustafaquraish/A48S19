<!-- {% raw %} -->

# Week 6 tutorial

-----

## Assignment 1 Overview

---

- The assignment deadline is going to come up soon, and you're on the clock! 

- Make sure you started implementing the assignment - or at the very least looked over it carefully and thought about how you would implement all the functions.

- Leaving time for yourself to test your code is very important. There may be bugs you have not yet noticed that come up when you're testing - you want to have time to be able to fix them properly.

---

What would be the output if you ran the following commands in order?

```bash
  0. penup               |    9. left
  1. forward 100         |   10. forward 200
  2. right               |   11. right
  3. forward 100         |   12. forward 100
  4. left                |   13. right
  5. pendown             |   14. forward 300
  6. forward 100         |   15. right
  7. right               |   16. forward 300
  8. forward 200         |   
```

Ask yourself this - what sort of things could you *not* draw using the assignment?

-----

## Dynamic Memory Management

---

- You have now learned in lecture how to allocate memory yourself on the heap using `calloc`. 
- This is called dynamic memory management since you as the programmer can choose when to allocate / free the memory, as opposed to it being done automatically based on the scope of the variables.

---

Lets do some review - answer these questions:
- What does `calloc` do, and how do you use it?
- Why do you need to use `calloc` at all?
- Where does this come up in the context of linked lists?

---

What will be the output when we run this code?
```c
double *random_array(void) {
  // This function sets up an array and fills it up with
  // random numbers, then returns the array for use outside.
  double random_nums[100];

  for (int i=0; i<100; i++)
    random_nums[100]=((double)rand()/(double)RAND_MAX);

  return &random_nums[0];
}
```
```c
int main() {
  double *randomnums=NULL;
  randomnums=random_array();

  printf("We got random numbers!\n");
  for (int i=0; i<100; i++) {
    printf("%lf\n",*(randomnums+i));
  }
  printf("\n");
  return 0;
}
```




---


- The code clearly has an issue! `random_nums` is a local variable, and as soon as the function returns, the memory for the array is cleared. 

- Even though you have a pointer to it, the memory it is pointing to is now invalid, and you might get unexpected results (or a segmentation fault). Try it!

---

- One way to solve this problem is to declare the array in main and then pass in a pointer to it to the function, so that the random numbers could be stored there. 

- However, an (arguably) nicer way to do this would be to use dynamic memory management, since this way you don't have to worry about creating the array everytime you want to call the function. 

- While we're at it, let's also pass in a number saying what size of array we want! 

---

Complete the following code:

```c
double *random_array_good(int N) {
  // Allocate and return an array with N random numbers

}
```
```c
int main() {
  double *randomnums=NULL;

  // Call the function to generate an array of 100 numbers


  printf("We got random numbers!\n");
  for (int i=0; i<100; i++) {
    printf("%lf\n",*(randomnums+i));
  }
  printf("\n");

  // Missing something here?
  return 0;
}
```

---

Now, the question is, does the chunk of memory allocated by `calloc` have a type?

- The answer is no! Remember that it returns `void *` 
- Neither `calloc`, the compiler, nor your computer care what you do with the memory. 

---

Look at the following (perfectly legal) code, and try to see what it does:

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
  char *char_data=NULL;
  int *int_data=NULL;
  void *data=NULL;

  // What do these 2 lines do?
  int_data=(int *)calloc(1000,sizeof(int));
  for (int i=0; i<1000; i++) *(int_data+i)=i;
```
```c

  // Now what do these 2 lines do?
  char_data=(char *)int_data;
  for (int i=0; i<1000; i++) *(char_data+i)='A';

  return 0;
}
```


---


Now, answer the following questions:

- Why can we just take the address of the integer array, convert it to `char *` and use it to store characters?
- *How many* characters can we store in the array? Why? How would we find out?

---

The bottom line is - memory chunks allocated with `calloc` can be used however we like, and it's up to our program to know what type of data it wants to put there, and how much it can store with what it reserved.

-----

## Additional exercises

---

- Write a function that takes in a number `N` and returns the head of linked list of size `N`. Each node should store a number, and the `i-th` node in the linked list should have the number `i` stored in it. Define an appropriate CDT to do this.

---

- Write a function that takes in appropriate sizes and dynamically allocates a two dimensional array. Initialize the array such that `arr[i][j] = i + j*j`. (We talked about how to store a 2-dimentional array as a 1-dimensional array last tutorial!)

---

- Do your exercise 2 using `calloc`! Make it so that all the input strings are not changed, and you should instead allocate the correct amount of memory for the output string, and then return a pointer to it.
<!-- {% endraw %} -->