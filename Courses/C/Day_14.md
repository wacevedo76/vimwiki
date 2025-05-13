* [Syllabus](./C-Syllabus.md)  
* [Table of contents](./index.md)  
* [Day 13](./Day_13.md)  
* [Day 15](./Day_15.md)  

# Day 14: Exercises (factorial using recursion, swapping two variables with pointers)

* ChatGPT Prompt
```
Okay, I think I am ready for Day 14: Exercises (factorial using recursion, swapping two variables with pointers). I would like you to  
generate a tutorial  for me in this format:

  * An introduction.
  * A summary,
  * A concise explanation of all the points listed in a summary.
  * A detailed explanation of all the points listed in the summary
  * a series of exercises that would help me learn the concepts holistically, 
    making note to point out any additional information I might need to accomplish 
    the tasks from the exercises. 
* And a Recap and Next Steps section 
```

* ChatGPT said:
```
Updated saved memory
Awesome — welcome to Day 14 of your C programming journey! You're now ready to reinforce your understanding of recursion and pointers through some practical and classic exercises.

Here’s your tutorial in the format you requested:
```

## 🧭 Introduction
In today’s lesson, you’ll revisit two of the most foundational and skill-reinforcing exercises in C:

* Implementing a **recursive factorial** function
* Swapping the values of two variables using **pointers**
* These exercises are often used in interviews and textbooks because they bring together key concepts like **control flow, memory management, recursion, and function parameters**.

## 📌 Summary
Today you'll learn:
* How recursion works in practice (via the factorial problem)
* How to pass values by reference using pointers
* How to swap variable values through pointer manipulation
* Why recursion requires a base case and stack frames
* When to choose recursion vs. iteration

## 📘 Concise Explanation of Concepts
1. Recursion
A function that calls itself to solve a smaller instance of a problem.
Used in problems with natural "repetition" or "division," like factorial or traversals.

2. Pointer-based Variable Swapping
Passing pointers to a function lets you modify the actual variables, not just copies.
Used when you want a function to change external state.

3. Base Case in Recursion
A condition that stops the recursion. Without it, the function would call itself forever and crash (stack overflow).

4. Call Stack
Each recursive call adds a frame to the call stack, holding its own local variables and state. These are unwound as the recursion returns.

## 🧠 Detailed Explanation
### 🔁 1. Recursive Factorial
Factorial is defined mathematically as:

```
n! = n × (n - 1) × (n - 2) ... × 1
```
And recursively as:

```c
int factorial(int n) {
    if (n <= 1) return 1;       // Base case
    else return n * factorial(n - 1);  // Recursive case
}
```
Each function call pushes a new frame on the stack until the base case is reached, then they resolve backward.

### 🔄 2. Swapping Two Variables (Pointers)
Swapping values without pointers won’t work:

```c
void swap(int a, int b) {
    int temp = a;
    a = b;
    b = temp;
}
// won't affect the originals in main!
```
Using pointers fixes this:

```c
void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}
```
Now, you call it with:

```c
swap(&x, &y);
```
This lets you modify the original variables because you’re working with their addresses.

## 🧪 Exercises
### ✅ Exercise 1: Recursive Factorial
* Write a function `int factorial(int n)`
* Test it with `factorial(5)` (should return `120`)
* Add error handling for negative input

### ✅ Exercise 2: Iterative Factorial (Compare)
* Write an iterative version of factorial
* Compare how recursion and iteration behave differently in terms of code and performance

### ✅ Exercise 3: Pointer-based Swap
* Write a `swap(int *a, int *b)` function
* Use it in `main()` to swap two integers
* Print the variables before and after swapping to verify

### ✅ Exercise 4: Swap Without a Temporary Variable (Challenge)
* Try to swap two integers using only arithmetic:

```c
*a = *a + *b;
*b = *a - *b;
*a = *a - *b;
```
* Be cautious: this works only when there’s no overflow

### ✅ Exercise 5 (Bonus): Recursive Power Function
* Write `int power(int base, int exp)` using recursion
* Handle `exp = 0` as the base case
* Optionally handle negative exponents (as an advanced challenge)

## 🔄 Recap and Next Steps
### 🧠 What You Learned:
* How to build and trace a recursive function
* Why base cases are essential to recursion
* How to pass variables by reference with pointers
* How to use pointer arithmetic for variable manipulation

## 🚀 Next Steps:
* Day 15: Arrays and strings in depth
    * Learn how strings are managed in C using null-terminated arrays
    * Understand memory layout and character pointers
* Optional:
    * Try writing a recursive version of the Fibonacci function (or improve your old one with memoization)
    * Write a general-purpose `swap` macro or function that works with any data type

Would you like help working through one of today’s exercises interactively? I can give you test cases or help step through your solution line by line.
