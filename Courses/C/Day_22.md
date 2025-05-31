* [Syllabus](./C-Syllabus.md)  
* [Table of contents](./index.md)  
* [Day 21](./Day_21.md)  
* [Day 23](./Day_23.md)  

# Day 22: Dynamic memory allocation (malloc, calloc, realloc, free)

## 1. Introduction
Dynamic memory allocation lets your C programs request memory during runtime. Unlike static arrays, you can decide the size of data structures like arrays at runtime. This is crucial for flexibility, efficiency, and building complex data structures (like linked lists and trees).

## 2. Summary
Key concepts for today:
* `malloc()` — allocate memory dynamically.
* `calloc()` — allocate and zero-initialize memory.
* `realloc()` — resize previously allocated memory.
* `free()` — deallocate memory.
* Common pitfalls and safe practices.

## 3. Concise Explanations
| Keyword   | Description                                 |
| --------- | ------------------------------------------- |
| malloc()  | Allocates memory but doesn’t initialize it. |
| calloc()  | Allocates and zeroes out memory.            |
| realloc() | Resizes previously allocated memory.        |
| free()    | Frees dynamically allocated memory.         |

## 4. Detailed Explanations
### 🔹 `malloc()` — Memory Allocation
```c
int *arr = (int *)malloc(5 * sizeof(int));
````
* Allocates memory for 5 integers.
* Returns a `void*`, so cast it.
* Memory is uninitialized (contains garbage).

### 🔹 `calloc()` — Cleared Allocation
```c
int *arr = (int *)calloc(5, sizeof(int));
```
* Similar to malloc() but sets all bits to 0.
* Useful when you need an initialized array.

### 🔹 `realloc()` — Resize Allocated Memory
```c
arr = (int *)realloc(arr, 10 * sizeof(int));
```
* Tries to expand or shrink the block.
* If needed, moves it to a new location.

### 🔹 `free()` — Deallocate Memory
```c
free(arr);
```
* Prevents memory leaks.
* Always free what you `malloc`, `calloc`, or `realloc`.

### 📦 Metaphor:
Imagine memory like a warehouse:
* `malloc` is renting boxes—what’s inside is unknown.
* `calloc` is renting empty boxes—clean and ready.
* `realloc` is expanding or reducing your storage space.
* `free` is vacating the boxes to avoid clutter and costs.

## 5. Exercises
### 🟢 Easy
1. Write a program that allocates an array of 10 integers using malloc, initializes it, prints it, and frees it
2. Allocate an array of 20 floats using calloc and confirm all values are zero.

### 🟡 Medium
3. Ask the user for an integer n, then dynamically allocate an array of n integers, fill it with values, and print the contents.
4. Allocate an array with malloc, then resize it using realloc to hold more integers and initialize the new elements.

### 🔴 Hard
5. Write a program that asks the user for names (strings), stores them in dynamically allocated memory, and prints them back.
6. Simulate a dynamic stack: let the user push integers to a dynamically resized array, and pop them.

## 6. Recap and Next Steps
### Today you learned:
* How to dynamically allocate, resize, and deallocate memory.
* When to use `malloc`, `calloc`, `realloc`, and `free`
* Safe practices to avoid memory leaks or segmentation faults.

### Next Steps:
* Practice building dynamic data structures (Day 23: Strings and Dynamic Arrays).
* Learn how to use dynamic memory in structs and linked lists.
* Optional: Explore Valgrind to detect memory leaks.
