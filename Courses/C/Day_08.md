* [Table of contents](./index.md)  
* [Syllabus](./C-Syllabus.md)  
* [Day 9](./Day_09.md)  

# The C programming language - Day 8: Function declaration, definition, and calling functions
ChatGPT Prompt:  
```
Okay, I'm ready for - Day 8: Function declaration, definition, and calling 
functions

Can you generate a summary of what day 8 entails, and afterwards generate a set 
of activities that would help me learn the concept of say 8 holisticly?
```

## 📌 Day 8: Functions in C (Declaration, Definition, and Calling)
### 🔹 Summary of Day 8
Today, you'll dive into functions, one of the most fundamental building blocks of C programming. Functions help organize your code, make it reusable, and improve readability.  

By the end of the day, you should understand:
1. Function Declaration (Prototype) – Tells the compiler about a function before it’s used.
2. Function Definition – The actual implementation of the function.
3. Function Calling – Using the function in main() or other functions.
4. Return Values and Parameters – Functions can return values or take inputs.
5. Void Functions – Functions that do not return anything.

## 🎯 Activities for Day 8
Here’s a set of hands-on activities to help you deeply understand functions in C.

### 1️⃣ Write and Call a Simple Function
✅ Create a function that prints a greeting message.
Example:

```c
#include <stdio.h>

void greet() {
    printf("Hello! Welcome to C programming.\n");
}

int main() {
    greet();  // Function call
    return 0;
}
```

## 📌 Modify the function to print the user's name.

### 2️⃣ Functions with Parameters
✅ Write a function that calculates the square of a number.
Example:

```c
#include <stdio.h>

int square(int num) {
    return num * num;
}

int main() {
    int num = 5;
    printf("Square of %d is %d\n", num, square(num));
    return 0;
}
```
## 📌 Extend this by writing a function for the cube of a number.

### 3️⃣ Functions with Multiple Parameters
✅ Write a function that takes two numbers and returns their sum.
Example:

```c
int add(int a, int b) {
    return a + b;
}
```

## 📌 Modify this to also return subtraction, multiplication, and division results.

### 4️⃣ Functions Returning void
✅ Write a function that prints a formatted message.
Example:  

```c
void printMessage() {
    printf("This is a function with no return value.\n");
}
```

## 📌 Modify it to take user input and print a custom message.

### 5️⃣ Function Challenge: Calculator with Functions
✅ Rewrite your calculator program from Day 7 but use separate functions for:  
* Addition
* Subtraction
* Multiplication
* Division
* Getting user input

## 📌 Bonus Challenge: Add error handling for division by zero.

### 6️⃣ Debugging Exercise
I can provide buggy function code that you have to fix. Let me know if you want some debugging challenges! 🛠️


