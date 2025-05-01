* [Syllabus](./C-Syllabus.md)  
* [Table of contents](./index.md)  
* [Day 12](./Day_12.md)  
* [Day 14](./Day_14.md)  

# Day 13: Function pointers
Excellent! You're stepping into one of C’s most powerful (and underrated) features: **function pointers**. This is the foundation of callbacks, dispatch tables, and even rudimentary polymorphism in C.

Here’s your Day 13: Function Pointers tutorial in the format you requested:

## 📌 Summary
Today you’ll learn:
1. What a function pointer is.
2. How to declare and assign a function pointer.
3. How to call a function through a pointer.
4. How to pass function pointers to other functions.
5. How to use function pointers for callbacks and simple control structures.

## 📘 Introduction
In C, just like variables have addresses, **functions also live at specific memory addresses**. A **function pointer** is a variable that stores the **address of a function**. You can use this pointer to call the function indirectly — which is especially useful for building flexible and reusable code.

Think of it like this:

    Just as you can pass a pointer to an `int`, you can pass a pointer to a 
    function that returns an `int`.

## 🧠 Concepts Explained
1. **What Is a Function Pointer?**
A function pointer is a variable that points to the **location of a function in memory**, allowing you to **call the function through the pointer**.

2. **Declaring a Function Pointer**
Syntax:

```c
return_type (*pointer_name)(parameter_types);
```
Example:

```c
int add(int a, int b) { return a + b; }
int (*fptr)(int, int) = &add;
```
3. **Calling a Function Through a Pointer**
You can call the function using:

```c
(*fptr)(2, 3);  // or just fptr(2, 3);
````
Both are valid. The extra `*` makes it explicit you’re dereferencing.

4. **Passing Function Pointers to Functions**
You can pass function pointers as arguments:

```c
void compute(int x, int y, int (*op)(int, int)) {
    printf("Result: %d\n", op(x, y));
}
```
5. **Using Function Pointers for Control Logic**
Instead of a `switch` or `if`, you can use an array of function pointers:

```c
int (*operations[])(int, int) = { add, subtract, multiply };
operations[0](2, 3);  // Calls add
```
This is super useful in interpreters, menu systems, or plugin architectures.

### 🧪 Exercises
#### ✅ Exercise 1: Basic Function Pointer
* Define a function `int add(int, int)`.
* Declare a pointer to it and use the pointer to call the function with `2` and `3`.

#### ✅ Exercise 2: Passing Function Pointer to Another Function
* Create `void compute(int, int, int (*)(int, int))`
* Pass in functions like `add,` `subtract`, `multiply`, and print the results.

#### ✅ Exercise 3: Array of Function Pointers
* Define three functions: `add`, `subtract`, `multiply`
* Create an array of function pointers and iterate through them
* Call each one with `(10, 5)` and print the results.

#### ✅ Exercise 4: Menu-Driven Calculator (Using Function Pointers)
* Use `scanf` to let a user choose an operation (`1: Add`, `2: Subtract, etc.`)
* Use an array of function pointers to map the choices to operations.

#### ✅ Exercise 5 (Bonus): Sort with a Callback
* Use `qsort()` (from `<stdlib.h>`) to sort an array of integers.
* Write your own comparator function and pass it as a function pointer.

```c
int compare(const void *a, const void *b);
```
#### 🧱 Helpful Notes
* Function pointer syntax can look weird — write them out slowly.
* Function pointers **must match the signature** (return type + parameters).
* When in doubt, break it down:

```c
int (*f)(int, int);   // f is a pointer to a function returning int
```
