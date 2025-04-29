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

#### How to calculate the size of an Array
In C, arrays don't "remember" their own size once you pass them around - **you have to keep track manually**. **Inside the same function** were the array is declared (where it's still a "true" array, not a pointer), you can calculate the number of elements like this:  
```c
int arr[5] = {1, 2, 3, 4, 5};
int size = sizeof(arr) / sizeof(arr[0]);
```

✅ How it works:
* `sizeof(arr)` gives the **total size** of the array in bytes.
* `sizeof(arr[0])` gives the **size of one element** (like one `int`).
* Dividing them tells you **how many elements** there are.

##### ⚡ Important:
Once you pass an array to a function, it `decays into a pointer`, and you lose the ability to use sizeof like this.  
So **if you need the size**, you should either:
* **Calculate it first** and **pass it as an argument**, or
* **Use a sentinel value** (like a special value to mark the end — common with strings using the `'\0'` character).

### 🌟 Solution for problems to  use for learning: Using a `while` loop with pointers

```c
#include <stdio.h>

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int *ptr = arr + 4; // Point to the last element (index 4)

    while (ptr >= arr) { // As long as ptr hasn't gone past the beginning
        printf("%d\n", *ptr);
        ptr--; // Move backward through the array
    }

    return 0;
}
```
#### 🔎 Key ideas:
* `arr` is the pointer to the first element.
* `arr + 4` is the pointer to the fifth element (index 4).
* We check `ptr >= arr` to stop when we've gone past the beginning.

#### 🌟 Solution 2: Using recursion
```c
#include <stdio.h>

void printReverse(int *start, int *end) {
    if (end < start) {
        return; // base case: if end pointer is before start pointer, stop
    }

    printf("%d\n", *end); // Print current value
    printReverse(start, end - 1); // Move one step back
}

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int *start = arr;             // Start of array
    int *end = arr + 4;            // End of array (5 elements, so arr + 4)

    printReverse(start, end);

    return 0;
}
```

#### 🔎 Key ideas:

* Base case: when `end < start`, stop.
* Recursively print current value, then move the pointer one step back.
* **No loops at all** — only recursion and pointer manipulation.

#### ⚡ Summary of Differences:

| Method     | How it works                               | Pros / Cons                          |
| ---------- | ------------------------------------------ | ------------------------------------ |
| While loop | Moves pointer backwards each step          | Simpler, slightly faster             |
| Recursion  | Moves pointer backwards via function calls | Elegant, but more memory stack usage |

### Additional Notes
#### 🤔 What is ptr (without the asterisk)?
```c
int arr[] = {1, 2, 3, 4, 5};
int *ptr = arr + 4;
```
In this context:
* `ptr` is a pointer variable of type `int *`
* It stores a **memory address**
* Specifically, it holds the address of `arr[4]`

#### 🧠 You can think of it like this:
Expression | Meaning
| ptr    | The address stored in the pointer — the location in memory |
| `*ptr` | The value at that address — the data ptr points to         |

So in your example:

```c
int *ptr = arr + 4;
```

* `ptr` is now holding the memory address of `arr[4]`.
* `*ptr` gives you the value stored in that memory address (which is `5`).

You can **print** both:

```c
printf("Address: %p\n", (void*)ptr);
printf("Value: %d\n", *ptr);
```
#### 🧪 Visual Breakdown:
Let's say this is how the array is laid out:

| Index  | Address (fake) | Value |
| ------ | -------------- | ----- |
| arr[0] | 0x1000         | 1     |
| arr[1] | 0x1004         | 2     |
| arr[2] | 0x1008         | 3     |
| arr[3] | 0x100C         | 4     |
| arr[4] | 0x1010         | 5     |

So if you write:

```c
int *ptr = arr + 4;
```
Then:

* `ptr` == 0x1010
* `*ptr` == 5

📌 Summary
| Term | What it gives you             | Type  |
| ---- | ----------------------------- | ----  |
| ptr  | Memory address (pointer)      | int * |
| *ptr | Value at that memory location | int   |

#### [✅](✅) This duality — the idea that a pointer can both store a memory location and give you access to the data there — is the essence of pointer power in C.

