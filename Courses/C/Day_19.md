* [Syllabus](./C-Syllabus.md)  
* [Table of contents](./index.md)  
* [Day 18](./Day_18.md)  
* [Day 20](./Day_20.md)  

# Day 19: Pointers and arrays (relationship between pointers and arrays)

**Welcome to Day 19: Pointers and Arrays — Understanding Their Relationship.** Today’s lesson dives into one of the most essential and powerful aspects of C: how arrays and pointers are tightly connected, and how this relationship enables low-level control and high-performance programming.

## 📘 1. Introduction
In C, arrays and pointers are often used interchangeably — but they are **not the same thing**. Understanding their relationship allows you to:
* Traverse arrays using pointer arithmetic
* Pass arrays to functions more efficiently
* Avoid bugs and segmentation faults
* Write cleaner, faster, and more memory-efficient code

This is a core concept in systems programming, embedded development, and C-based APIs.

## 📋 2. Summary
By the end of this lesson, you’ll be able to:
1. Understand how arrays and pointers are related in memory
2. Use pointer arithmetic to navigate arrays
3. Pass arrays to functions using pointers
4. Distinguish between array indexing and pointer dereferencing
5. Recognize where arrays decay into pointers
6. Avoid common mistakes like pointer out-of-bounds errors

## ✍️ 3. Concise Explanations
| Concept                     | Description                                                          |
| --------------------------- | -------------------------------------------------------------------- |
| Array name as pointer       | The array name (e.g., `arr`) points to the first element (`&arr[0]`) |
| Pointer arithmetic          | You can use `ptr + i` to move across an array                        |
| `*ptr` vs. `arr[i]`         | Both access the same memory; `arr[i]` is shorthand for `*(arr + i)`  |
| Passing arrays to functions | Arrays automatically decay to pointers when passed to functions      |
| Arrays vs. pointers         | Arrays occupy fixed memory; pointers can point anywhere              |

## 🔍 4. Detailed Explanations
### 🔸 1. Array name is a pointer to its first element
```c
int arr[] = {10, 20, 30};
int *p = arr;         // Same as: int *p = &arr[0];

printf("%d\n", *p);   // → 10
```
* arr is not a pointer variable, but it decays to &arr[0] in expressions.

### 🔸 2. Pointer Arithmetic
```c
int arr[] = {10, 20, 30};
int *p = arr;

printf("%d\n", *(p + 1));  // → 20
```
* p + 1 points to the second element (arr[1]).
* `*(p + i)` is equivalent to arr[i].

### 🔸 3. Arrays in Functions
```c
void printArray(int *a, int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", a[i]);  // or *(a + i)
    }
}
```
Call it like:
```c
Copy code
int nums[] = {1, 2, 3};
printArray(nums, 3);  // nums decays to &nums[0]
````

    ⚠️ Arrays don’t carry size info — you must pass it manually.

### 🔸 4. `arr[i]` is syntactic sugar for `*(arr + i)`
```c
int arr[] = {5, 10, 15};
printf("%d\n", arr[2]);        // → 15
printf("%d\n", *(arr + 2));    // → 15
```

### 🔸 5. Arrays are fixed blocks; pointers are flexible
```c
int arr[] = {1, 2, 3};
int *ptr = arr;          // points to arr

int vals[] = {4, 5, 6};
ptr = vals;              // now points to vals — but arr still points to its original array
````
* `ptr` is flexible.
* `arr` is not assignable: `arr = vals;` ❌ invalid.

🧠 Analogy: Train Track
Array → a fixed train track with numbered cars.
Pointer → a person walking along the track.
`arr[i]` = hop to car `i`
`*(arr + i)` = same thing using arithmetic

📐 ASCII Diagram
```c
int arr[] = {10, 20, 30};

Memory:

[arr[0]] [arr[1]] [arr[2]]
  ↓        ↓        ↓
 &arr[0]  &arr[1]  &arr[2]

arr → &arr[0]
arr + 1 → &arr[1]
*(arr + 2) → 30
````

## 🧪 5. Exercises
### 🟢 Easy
1. Declare an array of 5 integers and print its elements using both indexing and pointer arithmetic.
2. Use a pointer to iterate through an array and print the memory address of each element.

### 🟡 Medium
3. Write a function that takes an array and its size, and prints each element using `*(arr + i)` notation.
4. Copy an array into another using only pointers (no `arr[i]` notation).

### 🔴 Hard
5. Write a function that finds the maximum value in an array using pointers.
6. Implement a pointer-based version of `memcpy`: copy N elements from `src` to `dest`.

## 🧾 6. Recap and Next Steps
### ✅ Today You Learned:
* The close connection between arrays and pointers in C
* How pointer arithmetic lets you walk through arrays
* That `arr[i]` and `*(arr + i)` are interchangeable
* How arrays “decay” into pointers when passed to functions
* The differences between array variables and pointer variables

### 🔜 Coming Up Next:
**Day 20: Dynamic Memory Allocation with `malloc`, `calloc`, `realloc`, and `free`**

You’ll move from static arrays to **heap-allocated memory**, and learn how to manage memory manually — a crucial skill for larger programs and system-level work.
