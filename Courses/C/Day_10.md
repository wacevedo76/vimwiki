* [Table of contents](./index.md)  
* [Syllabus](./C-Syllabus.md)  
* [Day 9](./Day_09.md)  
* [Day 11](./Day_11.md)  

# Day 10: Recursion
Question to ChatGPT:
```
Okay, I am ready for Day 10: Recursion. Can you format the day's learning content as:
  * A summary of what day 10 entails.
  * The contents of each summary item.
  * A series of activities to help me learn the contents of today's learning 
    objectives holistic?

```

## Summary
Recursion is a programming technique where a function calls itself to solve smaller instances of a problem. It's especially useful for tasks that can be broken down into similar subtasks, like factorials, Fibonacci sequences, and tree traversals.

## Learning Contents
1. **What is Recursion?**
* A function is recursive if it calls itself.
* Every recursive function has:
    * **Base case**: condition under which the function stops calling itself.
    * **Recursive case**: the part where the function calls itself.

**Example**:
```c
void countdown(int n) {
    if (n == 0) {
        printf("Liftoff!\n");
    } else {
        printf("%d\n", n);
        countdown(n - 1);
    }
}
```
2. **Recursive vs. Iterative**  
* Recursive solutions may be more readable and elegant.
* Iterative solutions often use loops and may be more memory-efficient.
* Recursion uses the call stack, which can lead to stack overflow for deep recursion.

3. **Common Use Cases**
* Mathematical functions: factorial, Fibonacci, GCD (Greatest Common Divisor)
* Data structures: tree traversal, searching, sorting (like merge sort, quicksort)
* Backtracking problems

4. **Stack Memory and Recursion**
* Each recursive call adds a new frame to the call stack.
* When the base case is met, the stack begins to unwind.
* Tail recursion (a specific kind) can be optimized by some compilers.

## Activities
**Activity 1: Simple Countdown**  
Write a recursive function to count down from a number to 0, then print “Done!”

**Activity 2: Factorial Function**  
Write a function that calculates the factorial of a number using recursion:

```c
int factorial(int n);
```
**Activity 3: Fibonacci Sequence**  
Write a recursive function to return the nth Fibonacci number:

```c
int fibonacci(int n);
```
Bonus: Try the iterative version too and compare performance.

**Activity 4: Recursion vs Iteration**  
Solve the same problem (e.g., computing factorial or sum of natural numbers) using both recursion and iteration. Analyze memory usage and readability.

**Activity 5: Print Digits of a Number**  
Write a recursive function that prints each digit of an integer:

```yaml
Input: 1234
Output: 1 2 3 4
```
**Challenge Activity**  
Implement a recursive function to calculate the Greatest Common Divisor (GCD) of two integers using Euclid's algorithm.
