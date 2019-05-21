<!-- {% raw %} -->

# Week 3 Tutorial 


-----

## Working with Arrays

---

- In this exercise, we will write a program that takes in an array of numbers, and then computes the sine and cosine of these numbers using the **`sin()`** and **`cos()`** functions of the math library. 

- We will use *only array notation* (no pointers for now).


---

Complete the following functions:

```c
#include<math.h>

// Complete the prototype. What parameters are needed?
void computeSineCosine( ... parameters ... ) {
  // Complete this function!

}
```
```c
int main() {
  //  - First, Declare an array 'array' with 10 floating 
  //     point numbers. Fill up this array with numbers 
  //     such that       array[i] = (2 * pi * i) / 10

  //  - Then, declare 2 arrays 'sin_theta' and 'cos_theta', 
  //    both having 10 floating point numbers each.

  //  - Finally, call the computeSineCosine() which computes
  //    the sine and cosine of all the numbers in 'array'

  return 0;
}
```

---


- After you're done with this, draw out the memory model on a piece of paper and trace the code to make sure you really understand how this works in memory.

- You should know how your function is getting access to the arrays, and how the computed values are being stored.

---

### This is important!

- Understanding how arrays work properly is going to be something that will be useful to you for the rest of your programming career in C, and can help you avoid a lot of common mistakes.

-----

## Using pointers!


---

- Now, complete the same exercise as before, except using pointers instead of array notation. (Your function will now take in pointers).

---

Remember this pointer notation:
- Get the address using the **`&`** operator. **`&array[5]`** gets the address of the 6<sup>th</sup> entry in **`array`**.

- Accessing information using the **`*`** operator. **`*(p)`** is accessing the location whose address is in **`p`**.

- We can replace **`(p)`** with expressions that modify the address. **`*(p+3)`**  is accessing the location whose address is **`p+3`**


---

Once you're done with this, make sure you can answer the following questions:

- How would these programs be different if you traced the memory model?

- What's the difference between using pointers vs. using arrays?

- In this case, or in general, should you be using pointers or arrays? Why?

-----

## *Some technical issues*

---

- The **`sin()`** and **`cos()`** functions are part of the math library, which are not available to you by default. To use these functions, you need to include the math library using 

**```#include<math.h>```**


---

- When compiling your code with the math library included, you need to add the ***`-lm`*** flag. 

- This tells the compiler to **l**ink the **m**ath library, which means it will find and include it when compiling your program. 

- For example, instead of **`gcc file.c`**, we would now compile with **`gcc file.c -lm`**. Without this, you may get an error.

---

- The math library is one of the most used ones available, with a host of different functions and constants you can use! 

- You should look up what else is available to use, it may be helpful to you when programming in C - there's no need to reinvent the wheel.


-----

## The `const` modifier


---

- Passing an array or a pointer to an array to a function gives the it full power to change data in that array. 

- What if we want to give a function access to the contents of the array, but not let it modify the data?

- This is where the **`const`** modifier comes in. We use it in a variable declaration to say that this variable cannot be modified. 


---

For instance, if we use the example in the exercises earlier, we would now declare our function as follows:

```c
void computeSineCosine(const float array[10], ... ) { ... }
```


- This declaration says that **`array`** is going to be treated as a constant inside the function.

- This means that the function's code **will not be allowed** to change its contents *(by the compiler!)*. 

---

- This ensures that we can pass an array to a function without worrying about it being changed. 

- It's similar to the idea of immutable data in Python, except here we control exactly what is treated as a **`const`**, and what is not.

- *Would it make sense to declare the **`sin_theta`** and **`cos_theta`** parameters using **`const`**? Why / Why not?*

---

- You may have seen the **`const`** modifier before if you were looking at functions in the string library **`string.h`**. 

- It is used there often to ensure that the strings you are working on are not modified when you don't expect them to be.

---

As an exercise, for the following functions, which of the parameters should have a **`const`** modifier? Why?

- `strcpy(string A, string B)`

- `strcat(string A, string B)`

- `strlen(string A)`


-----

## Additional exercises


---

- Write a function **`countOccurences()`** that takes in a string as input, and counts the number of times each character appears in it. Think carefully about how you would return the result.

---

- Write a function **`stringConcatenate()`** that takes in 2 strings, and concatenates the 2<sup>nd</sup> string at the end of the 1<sup>st</sup> one. Do this using both arrays and pointers, and without using the **`string.h`** library.

---

- Write a function **`isSubstring()`** that takes in 2 strings, and returns **`1`** if the 1<sup>st</sup> string is a substring of the 2<sup>nd</sup> one, and **`0`** otherwise.

---

- Complete the following function:

```c
void replaceSubstring(char *str, char *a, char *b) {
  /* If 'a' is a substring of 'str', then the corresponding 
   * section of 'str' is replaced with 'b'.
   *
   * For example:
   *
   *       char str[50] = "Hello World!";
   *       replaceSubstring(str, "llo W", "---");
   *       printf("%s\n", str);
   *
   * should print out "He---orld!"
   */

 return;
}
```

<!-- {% endraw %} -->