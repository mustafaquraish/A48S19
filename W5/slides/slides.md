<!-- {% raw %} -->

# Week 5 tutorial

-----

## Compound data types (CDTs)

---

Since the Avengers showed up, there's been a lot more superheros showing up, and frankly - it's getting quite out of hand. 

We want to create a database of superheros to keep track of all of them. 

---

To do this, you need to design a CDT to store all the information about a superhero. You should:

- Decide what the fields should be (and their types).
- Declare all of these fields in your struct.
- Create the `typedef` for this struct and give it an appropriate name.

---

- Keep in mind that there's many different ways of storing the same information. 
- Some of these have advantages over the other.
- Ask your friends how they have chosen to design their data type, and discuss what the advantages/disadvantages of your approaches might be.

---

Now, in your `main()` function, 

- Declare a couple of variables of this data type, and also a pointer to this data type.
- Initialize one of the variables directly using the `.` operator.
- Initialize another one using the pointer and appropriate operator.
- Write a function that changes some of the fields of the structs you declared in your main function. (how would you do this?)

---

*Make sure you understand the difference between using a pointer to access a struct and accessing it directly. This will be very important later in the course.*

-----

## Nested compound data types

---

- Suppose we are designing a database to handle laptop orders for Dell. We're going to have a top-level CDT that contains information about a laptop a user ordered. 

Let's say it stores the following information:

- Model
- Memory amount
- Storage spec
- Graphics card spec
- CPU type

---

*Now, here's the kicker*

The **Storage spec** is itself a CDT that contains:
- Type of storage (HDD or SSD)
- Capacity
- Transfer speed

Also, the **Graphics card spec** is a CDT that contains
- Number of processing elements
- Clock speed
- Memory capacity
- Memory bandwidth

---

- Declare the top-level CDT, using appropriate field names and data types. 
- Also, declare **at least** one of the the `storage spec` or `graphics card spec` CDTs.

---

Now, in your main function, declare and initialize a laptop type variable (your top-level CDT). Answer the following questions:

- Do we need to separately declare storage spec and graphics card spec?
- How do we change the values in the storage spec/graphics card spec if we have a variable for the laptop CDT?
- How do we change the values in the storage spec/graphics card spec if we have a pointer for the laptop CDT?

---

*You're going to be using CDTs a *lot* for your upcoming assignments. Make sure you understand how all of this works, so you have an easier time doing those!*

-----

## Additional Exercises

---

- Create a linked list of superheros using the CDT you created above! Practice implementing the different operations you have learned about.

---

Vectors are something we often work with in computer science. 

- Write a CDT that represents a (3-dimensional vector), and then implement the functions `add()`, `scale()`, `dot()` to add 2 vectors, multiply a vector by a scalar value, and take the dot product of 2 vectors respectively. 

*What should the input and return types be for each of these functions?*

---

- Design and implement a CDT to represent a profile on the new social network "BaceFook". What information do you think should be stored in it?

 

<!-- {% endraw %} -->