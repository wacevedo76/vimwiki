* [Syllabus](./C-Syllabus.md)  
* [Table of contents](./index.md)  
* [Day 10](./Day_10.md)  
* [Day 12](./Day_12.md)  

# Day 11: Introduction to pointers `(*, &, NULL)`
### ChatGPT Prompt
```
okay, I think I am ready for Day 11: Introduction to pointers (*, &, NULL) I 
would like you to generate a tutorial  for me in this format:
* A summary,
* an introduction.
* Concise explanation of all the points listed in a summary.
* and a series of exercises that would help me learn the concepts holistically, 
  making note to point out any additional information I might need to accomplish 
  the tasks from the exercises. 
```
## 📌 Summary
In Day 11, you will learn:
1. What a pointer is.
2. The * operator (dereferencing).
3. The & operator (address-of).
4. The NULL macro and its purpose.
5. Why and when to use pointers in C.

### 📘 Introduction
Pointers are one of the most powerful—and challenging—features of the C 
language. They allow programs to directly manipulate memory, work efficiently 
with arrays and strings, and implement dynamic data structures like linked 
lists. Today, you'll be introduced to the basics of how pointers work, what they 
look like in memory, and how to use them safely.

### 🧠 Concept Explanations
1. What is a Pointer?
A **pointer** is a variable that holds the memory address of another variable.

Example:

```c
int a = 10;
int *p = &a;  // p holds the address of a
```
2. The `&` Operator (Address-of)
The `&` operator gives the **address** of a variable.

```c
int a = 5;
printf("%p\n", &a);  // prints the address of a
```
3. The `*` Operator (Dereferencing)
The `*` operator lets you access the **value** at the address a pointer is pointing to.

```c
int a = 5;
int *p = &a;

printf("%d\n", *p);  // prints 5
```
4. The `NULL` Macro
`NULL` is a constant used to represent a pointer that points to **nothing**. It's a safe way to initialize a pointer when you don’t yet have a valid address to assign to it.

```c
int *p = NULL;
```
5. Why Use Pointers?
* Efficiency: Avoid copying large data structures.
* Function arguments: Modify values inside functions.
* Dynamic memory allocation.
* Working with arrays and strings.

### 🧩 Exercises
#### 🧪 Exercise 1: Basic Pointer Assignment
Write a program that:
* Declares an integer variable and assigns a value.
* Declares a pointer to that variable.
* Prints the value and the address using both the variable and the pointer.

#### 🧪 Exercise 2: Value Manipulation Through a Pointer
Write a program that:
* Declares an integer variable.
* Assigns its address to a pointer.
* Modifies the value using the pointer.
* Prints the result using the original variable.

#### 🧪 Exercise 3: Function That Swaps Two Integers Using Pointers
Write a function:

```c
void swap(int *a, int *b);
```
* Call it from `main()` and demonstrate that it works.

#### 🧪 Exercise 4: Safe NULL Checking
Write a function:

```c
void printValue(int *ptr);
```
* If `ptr` is not `NULL`, print the value it points to.
* If `ptr` is `NULL`, print a warning message.
* Call the function with both a valid pointer and a `NULL` pointer.

#### 🧪 Exercise 5: Pointer and Array Relationship
Write a program that:
* Declares an array of integers.
* Uses a pointer to iterate through the array using pointer arithmetic.
* Prints each element and its address.

#### 🧱 Bonus Info You'll Need
* `%p` is the format specifier used for printing addresses.
* Remember to include `#include <stdio.h>` at the top.
* Always check for `NULL` before dereferencing a pointer.
* Use comments in your code to trace what's happening in memory.

### Additional Notes
#### 🧠 Part 1: Arrays in C
##### ✅ Declaring and Initializing an Array
```c
int arr[5] = {10, 20, 30, 40, 50};
```
This declares an array of 5 integers and initializes it.  

You can also declare it and assign later:

```c
int arr[5];
arr[0] = 10;
arr[1] = 20;
arr[2] = 30;
arr[3] = 40;
arr[4] = 50;
```
##### ✅ To access an element:
```c
printf("%d", arr[2]); // Prints 30
```
✅ The name of the array, arr, is actually a pointer to the first element.

#### 🔧 Part 2: Adding/Removing Elements
In C, arrays have fixed size, meaning you cannot dynamically grow or shrink them like in Python (`append`, `pop`, etc.). To manipulate arrays like you would in Python, you'd need to:
* Use a bigger array and manage the size manually
* Or use dynamic memory allocation (`malloc`, `realloc`, `free`), which comes later

But for now, let's focus on simulating some of these actions manually.

##### 🟡 Simulate Push (Add to End)
```c
arr[5] = 60; // Only works if you had space for arr[6]!
```

#####🟡 Simulate Insert (Add in Middle)
You’d have to **shift elements manually**:

```c
// insert 25 at index 2
for (int i = 4; i > 2; i--) {
    arr[i+1] = arr[i];
}
arr[2] = 25;
```
##### 🟡 Simulate Pop (Remove from End)
Just ignore the last element or overwrite it.

##### 🟡 Simulate Remove from Middle
Shift elements left:

```c
// remove element at index 2
for (int i = 2; i < 4; i++) {
    arr[i] = arr[i + 1];
}
```
These are manual operations. Arrays in C don't manage size for you!

#### 💥 Part 3: Pointer Arithmetic
##### ✅ Concept
* arr is a pointer to the first element
* You can use `*(arr + i)` to get the value at index i
* Pointer arithmetic moves in units of the type (e.g., int in this case)

```c
int *p = arr;

for (int i = 0; i < 5; i++) {
    printf("Value: %d, Address: %p\n", *(p + i), (p + i));
}
```
Each `(p + i)` points to the next element of the array. No need for bitwise or fancy tricks — pointer arithmetic in C takes care of moving to the next memory slot of the correct type.

##### 🧪 Let's Put It Together — Starter Code for Exercise 5
```c
#include <stdio.h>

int main() {
    int arr[5] = {10, 20, 30, 40, 50};
    int *p = arr;

    for (int i = 0; i < 5; i++) {
        printf("Element %d: Value = %d, Address = %p\n", i, *(p + i), (p + i));
    }

    return 0;
}
```
##### 🧭 Summary of Your Questions

| Concept            | In C                                        |
| ------------------ | ------------------------------------------- |
| Array declaration  | `int arr[5] = {1, 2, 3, 4, 5};`             |
| Add element        | Shift elements manually or preallocate room |
| Remove element     | Shift left/right manually                   |
| Pointer arithmetic | `*(ptr + i)` to access elements             |
| Pointer to array   | `int *ptr = arr;`                           |

