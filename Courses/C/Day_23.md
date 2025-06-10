* [Syllabus](./C-Syllabus.md)  
* [Table of contents](./index.md)  
* [Day 22](./Day_22.md)  
* [Day 24](./Day_24.md)  

# Day 23: Memory Leaks and Debugging Tools (Valgrind)

## 1. Introduction
Memory management in C is powerful but manual — and mistakes like forgetting to free memory can lead to memory leaks, which slow down or crash your programs over time. Tools like Valgrind help identify memory leaks and other memory-related bugs.

Understanding how to use these tools will make you a much more reliable and confident C developer.

## 2. Summary
Today you'll learn:
* What memory leaks are
* How to detect memory leaks using Valgrind
* How to fix common memory issues
* Introduction to memory error types
* Best practices to avoid memory leaks

3. Concise Explanations

| Concept                  | Explanation                                                              |
| ------------------------ | ------------------------------------------------------------------------ |
| Memory Leak              | Memory that was allocated with malloc, calloc, or realloc but not freed. |
| Valgrind                 | A command-line tool to detect memory leaks, invalid accesses, and more.  |
| `free()`                 | Used to release memory allocated with `malloc`/`calloc`.                 |
| Invalid Read/Write       | Accessing memory outside of what was allocated.                          |
| Uninitialized Memory Use | Using a variable before giving it a value.                               |

## 4. Detailed Explanations
🧠 What is a Memory Leak?
Every time you allocate memory dynamically using malloc, calloc, or realloc, you must release it with free(). Otherwise, the memory stays reserved until your program ends — or worse, never gets reclaimed.

    Metaphor: Imagine renting hotel rooms for variables, but never checking out — you’ll eventually run out of rooms.

### 🔧 Valgrind: Your Memory Detective
Valgrind helps you:
* Detect memory that wasn't freed
* Catch invalid memory accesses
* Find uninitialized values
* Install it on Arch Linux:

```sh
sudo pacman -S valgrind
```
Run it on your compiled C program:

```sh
valgrind ./your_program
```

### 🧪 Example: Memory Leak
```c
#include <stdlib.h>

int main() {
    int *data = malloc(100 * sizeof(int)); // allocated
    data[0] = 5;

    // forgot to free(data);
    return 0;
}
```
🐞 Output from Valgrind:
```python-repl
==12345== HEAP SUMMARY:
==12345==    definitely lost: 400 bytes in 1 blocks
...
```
This tells you that memory was lost — never freed.

### 🧪 Example: Invalid Read
```c
#include <stdlib.h>

int main() {
    int *arr = malloc(5 * sizeof(int));
    arr[5] = 10;  // Invalid write! Index 5 is out of bounds.
    free(arr);
    return 0;
}
```
🐞 Output from Valgrind:
```arduino
==12345== Invalid write of size 4
==12345==    at 0x4005F6: main (test.c:5)
### 
```

### 🧹 Best Practices
* Always pair each malloc/calloc/realloc with free().
* Set pointers to NULL after freeing.
* Avoid using pointers after free() (use-after-free error).
* Use tools like valgrind regularly during development.

## 5. Exercises
### 🟢 Easy
Task:
Write a program that allocates an array of 10 integers, assigns values, prints them, and then frees the memory. Run it with valgrind and ensure there are no leaks.

### 🟡 Medium
Task:
Write a function that creates and returns a dynamically allocated array of n integers. Use it in main(), and make sure to properly free the memory afterward.

Add an intentional bug: forget to free it, then find and fix it using Valgrind.

### 🔴 Hard
Task:  
Create a mini text-based menu where:
* Option 1 allocates a new array
* Option 2 fills and displays the array
* Option 3 frees the array

Use Valgrind to check for:
* Memory leaks
* Invalid accesses (try intentionally accessing freed memory once, and detect it)
* Bonus: Extend your menu system from Day 21 to integrate this behavior.

## 6. Recap and Next Steps
### ✅ You learned:
* How memory leaks happen and why they’re dangerous
* How to detect and fix them using Valgrind
* How to handle and validate dynamic memory allocation correctly

### 🔜 Up Next:
Day 24: Structures (struct) and Nested Structures
* Learn how to define and use custom data types
* Combine them with dynamic memory
* Begin modeling more complex data (like objects)

