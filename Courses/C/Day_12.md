* [Syllabus](./C-Syllabus.md)  
* [Table of contents](./index.md)  
* [Day 11](./Day_11.md)  
* [Day 13](./Day_13.md)  

# Day 12: Pointer arithmetic

**ChatGPT prompt**
```
Okay, I think I am ready for Day 12: Pointer arithmetic I would like you to  
generate a tutorial  for me in this format:

  * A summary,
  * An introduction.
  * A concise explanation of all the points listed in a summary.
  * and a series of exercises that would help me learn the concepts holistically, 
    making note to point out any additional information I might need to accomplish 
    the tasks from the exercises. 
```

## Summary
In this lesson, you'll learn:
* What pointer arithmetic is and how it works in C.
* How to use `+`, `-`, and comparison operators with pointers.
* How pointers relate to arrays and how to traverse arrays using pointer arithmetic.
* The difference between `*ptr++`, `(*ptr)++`, and `++*ptr`.
* How to avoid common pitfalls and undefined behaviors in pointer arithmetic.

## Introduction
In C, pointers do more than just store addresses — you can also perform arithmetic on them. This lets you walk through arrays, perform calculations with memory addresses, and build powerful and memory-efficient code. Pointer arithmetic is deeply tied to the way arrays and memory work in C. Once you understand the basics, you'll start seeing the power behind this concept, especially in lower-level tasks like buffer handling and data manipulation.

## Core Concepts
### 1. Pointer Arithmetic Basics
In C, you can do the following arithmetic operations on pointers:
* `ptr + 1`: Moves the pointer to the next element of its type.
* `ptr - 1`: Moves the pointer to the previous element.
* `ptr1 - ptr2`: Gives the number of elements between two pointers (if they point to the same array).

Example:

```c
int arr[3] = {10, 20, 30};
int *ptr = arr;

printf("%d\n", *(ptr + 1)); // Outputs 20
```
### 2. Pointers and Arrays
An array name like arr is essentially a pointer to the first element:

```c
int arr[5] = {1, 2, 3, 4, 5};
int *p = arr;

printf("%d\n", *p);       // Outputs 1
printf("%d\n", *(p + 2)); // Outputs 3
```

### 3. Incrementing Pointers
* `*ptr++` means: get the value, then move pointer forward.
* `(*ptr)++` means: increment the value pointed to.
* `++*ptr` means: increment the value pointed to before using it.

### 4. Pointer Comparisons
You can compare two pointers (e.g., `ptr1 < ptr2`) if they point to elements of the same array.

## Exercises
### Exercise 1: Basic Pointer Arithmetic
Create an integer array of 5 elements. Use a pointer to:
* Print each value using pointer arithmetic (`ptr + i`).
* Print each value's memory address.

### Exercise 2: Increment Variants
Create a pointer to an integer and practice these three expressions:
* `*ptr++`
* `(*ptr)++`
* `++*ptr` Use `printf` to observe the differences.

### Exercise 3: Reversing Array Traversal
Use a pointer to print the elements of an array in reverse without using a loop counter. Just rely on pointer manipulation.

### Exercise 4: Find Max Using Pointer Arithmetic
Write a function `int findMax(int *arr, int length)` that returns the maximum value in the array using only pointer arithmetic (no indexing like `arr[i]`).

### Exercise 5: Pointer Differences
Create two pointers into the same array and subtract them. Print the result and explain what it represents.

### Helpful Notes
* Pointer arithmetic automatically accounts for the size of the type. So `ptr + 1` on an `int*` actually moves `sizeof(int)` bytes.
* Avoid going out of bounds (e.g., `ptr + 5` if the array has only 5 elements). It leads to **undefined behavior**.
* Always initialize your pointers. Using uninitialized pointers is dangerous.

