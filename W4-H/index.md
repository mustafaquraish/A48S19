---
title: Week 4 Tutorial
# sidebar: 4
sidebar-title: Week 4
---

---
## Representing Data in memory
---

This week we'll be talking about how the data we work with in our programs is stored in memory. This is something that is important to understand, as it helps us better understand and avoid a lot of mistakes that we may not realize we are making. 

It also helps us begin to understand how complex it is for a computer to actually be operating. You will learn a lot more about this in your Computer Organization course (CSCB58) and Systems Programming (CSCB09) courses, however, understanding the basics here will help you become a better C programmer.

> Before we go any further, take a moment and ask yourself:
> - How do you think information is stored in memory? 

Everything in a computer is stored as bits. A bit *(short for binary digit)* is the smallest unit of data in computers - which can have the value of either `0` or `1`. This is because bits are really convenient to represent in a lot of ways, some of which include:

- Electric signals (on / off)
- Voltage values (high / low)
- Magnetic orientation (north / south)
- Holes in a CD (present / absent)

This allows us to make a variety of different digital storage devices using very different technology as long as we can somehow represent bits on them!

> You might think that this seems very limiting - since each bit can only store one of 2 possible values. So, the question you should be asking yourself is:
> - What sort of data can we represent using these bits?

Using a sufficiently long string of bits, and some clever encoding, we can represent **anything!** The only thing we need to figure out here is that for any type information, how do we come up with a way to *uniquely* represent each value or data we need to using only bits.

Let's look at how come common data types are represented in binary!

---
## Decimal numbers (integers)
---

Here's the first few (non-negative) integers represented in binary:

```
  value                  bits                 
-------------------------------
    0                    0000                 
    1                    0001                 
    2                    0010                          
    3                    0011                           
    4                    0100                           
```

Now, generalize this pattern, and write down the binary representation of all of the numbers up to 15 on a piece of paper to make sure you understand how this works.

Larger numbers work the same way, we just use more bits. You'll talk more about this in CSCB58, as well as how to deal with negative numbers. You don't have to worry about it for now.


Typically, integers in C consist of 32 bits, or 4 bytes. (1 byte = 8 bits)

---
## Characters
---

We talked about how characters have a numeric value, and how they can just be thought of as an integer value on which you can do mathematical operations. So, how are they actually stored in memory?

They key here is the ASCII table. For each character that can appear in text, the ASCII table lists a unique corresponding integer between 0 and 255. Here are some common examples:

```
  character           ASCII Value                 
-----------------------------------
    '\0'                    0                 
               ...                        
     'A'                   65
     'B'                   66
               ...
     'a'                   97
     'b'                   98
                ...  
```

Now, these ASCII values are simply integers, so they are encoded in the same way we described above, and then stored in memory as bits.

Each character uses 8 bits (or 1 byte) since you need at least that many to be able to store 256 different values. This has no particular significance other than that is what people thought would be
enough for standard text!


---
## Floating Point Numbers
---

Floating point numbers are much harder to store. We need to come up with a clever way to do this consistently, since we can have numbers that are very big, and also numbers that are very small. 

> What do you think is a good way to do this? (Hint: you have seen something like this before!)

We will use scientific notation! Consider the case where we are trying to store the number `3.141592` in memory. 

- First write it in the form `.3141592 * 10^1` (so that the first non-zero digit is immediately to the right of the decimal point)
- Now, we can separately convert `3141592` (as an integer) and `1` (which is the power of 10) to binary, and store them as bits.
- `3141592` here is called the 'mantissa' and `1` is called the 'exponent'

Let's look at another example. Let the number be `25.5`.

- First we write it as `.255 * 10^2`.
- Convert `255` and `2` to bits and store them.

As an additional exercise, what would be the mantissa and exponent when storing the number `0.00004357` in memory? (You don't need to convert them to binary).

Typically, 32 bits (4 bytes) are used for a `float`, and 64 bits (8 bytes) are used for a `double`. There are international standards that specify how many bits to use for the mantissa and exponent, you'll see all of that in CSCB58! 

---
## Images
---

We will start by looking at grayscale (black and white) images. The thing to note here is that every image is made of pixels. 

> How would you encode and store a grayscale image in memory?

For a grayscale image, each pixel has a brightness value between 0 (black) and 255 (white). Values in between both of these numbers are varying shades of gray, from almost black to almost white. We already know that we can store values from 0-255 in one byte, so we're going to need one byte per pixel.

Now, the question is, how do we store all the pixels in the image (which is 2-dimensional) into a string of bits (which is one dimensional). A common approach is to first store all the pixels in the first row, then all the pixels in the second row, etc. (This is called *row-major* order). 

You will see more of this on A1, where you'll be working with `.pgm` images, which use exactly this format to store the images!

> How would you now extend this idea to encode a colour image?

Every colour in an image can be made using some combination of the colours *Red*, *Green* and *Blue* (often called RGB). Now, for each pixel, insteading of storing one single value, we store a triplet of values, indicating the amount of R, G and B. Each of these values will range from 0-255, as before. Each pixel will now have 3 bytes of data. We store the triples in a similar way as the single values for grayscale.

---
## Sound Recordings
---

Now, lets try thinking of types of data that are harder to encode.

> How would you encode a sound recording in memory?

Sounds can be represented in many different ways on a computer. One way of doing it is storing the frequency (pitch) and amplitude (volume) of the sound at different points in time consecutively. If we have enough of these close to each other, it sounds like a continuous stream of audio! Each of these values can be encoded as floating point numbers (between -1 and 1) or integers (between 0 to 255, or -127 to 127) and then encoded as bits.

There are a lot more complex methods of encoding audio that are beyond the scope of what we are trying to cover right now, but it boils down to a similar principle at the end of the day. We can represent most things using an appropriate sequence of numbers (or equivalently, bits)!

---
## Computer Code
---

When we compile our C code, it is turned into CPU instructions. These are very simple instructions that tell the CPU exactly what it's supposed to be doing at any time. Lets look at a simple example (It's ok if you don't fully understand this!)

```python
  C instruction       CPU Instruction (MIPS 32)   
--------------------------------------------------
     x=x+1;              LW $t1,x          (1)
   
                         ADDI $t1,$t1,1    (2)
                                         
                         SW $t1,x          (3)
```
*(Note: MIPS 32 is a set of CPU instructions - you'll learn more about it in CSCB58!)*

Let's look at what each instruction here means:
1. `LW` is used to *load* information. We're loading the value of `x` into the CPU's memory (a register) called `t1` so we can manipulate it.
2. `ADDI` is used for addition. This line tells the CPU to add `1` to the value in the register `t1`.
3. `SW` is used to *store* information. We're saving the new value in the register `t1` back into the locker for `x`.

Now, we can encode the different pieces of each CPU instruction. 
- Each instruction has a unique integer ID, which we can encode in binary. 
- Each CPU register also has a unique integer ID.
- The arguments can also be stored in binary since they are either numbers (remember even characters are stored as numbers) or pointers (which are memory addresses, and also just numbers).

Here is an example of how the encoding would work:
```
     ADDI               $t1           $t1            1

--------------------------------------------------------------
 Instruction ID      Register ID    Register ID    Argument
      05                01             01            1
 
-------------------------- In bits ---------------------------
     0101              0001           0001          0001
```

Once again, the point of this example is to illustrate that we can store very complex data in memory by being smart about how we choose to encode it. It's ok to be a little lost here - you will learn all of this in depth in your upper year courses. 

---
## Having some fun!
---

Knowing what we just learned, try and figure out what this code does:

```c
#include<stdio.h>
#include<stdlib.h>

int main() {
  char stringy[7] = "Logic!";
  char *c;
  int *i;
  float *f;

  printf("My string says: %s\n",stringy);

  // Let's get a pointer to the string!
  c=&stringy[0];
  i=&stringy[0];
  f=&stringy[0];

  printf("Wait a sec, is it really a string?\n");
  printf("I think it may be a char! %c\n",*c);
  printf("Or perhaps it's an int??? %d\n",*i);
  printf("Or maybe a float?? %f\n",*f);

  printf("This gets really weird!\n");
  *i=1768382797;
  printf("My string says: %s\n",stringy);
  printf("What just happened!!!????\n");
 }
 ```

 Why does the code do this?
 
 ---
[Slideshow version](slides/)