---
title: Week 10 Tutorial
sidebar: 10
sidebar-title: Week 10
---

---
## The Problem
---

A lot of you have been having issues with pointers, memory allocation and segmentation faults while doing A2. It's sometimes hard to see what's going wrong using print statements in these cases, so we're going to look at a tool called valgrind that helps us analyze nd solve these problems.

---
## What is Valgrind?
---

Valgrind is a tool that is used to analyze the memory usage of your program. It essentially takes over the memory management, and tracks what you're doing with it. It does the following:

 * Check memory accesses in your code
 * Checks all array accesses
 * Checks every use of pointers
 * Checks that you release memory you reserved
 * Checks you're not using 'junk' data anywhere in your code

---
## How to use Valgrind
---

First, make sure you have valgrind installed. Guides should be easily available online. If you're on Windows, you will need to install the Ubuntu Subsystem to get valgrind. (Or install Linux).

---

Here's the basic usage of valgrind:

```
valgrind --verbose --leak-check=yes   ./program_to_check
```

Let's look at a few examples of code and run this together.

---

Example 1

```c
int main() {
  int array[10];

  for (int i=0; i<100000; i++)
    array[i]=i;

  return 0;
}
```
---

Example 2

```c
int main() {
  int *array;

  array=(int *)calloc(10,sizeof(int));
  for (int i=0; i<100000; i++)
    *(array+i)=i;

  return 0;
}
```
---

The error messages can be cryptic sometimes, so you might want to use the reference [here](http://valgrind.org/docs/manual/quick-start.html).

---
[Slideshow version](slides/), more on [debugging](../debug/).