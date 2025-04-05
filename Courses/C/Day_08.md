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
📌 Extend this by writing a function for the cube of a number.

### 3️⃣ Functions with Multiple Parameters
✅ Write a function that takes two numbers and returns their sum.
Example:

```c
int add(int a, int b) {
    return a + b;
}
```

📌 Modify this to also return subtraction, multiplication, and division results.

### 4️⃣ Functions Returning void
✅ Write a function that prints a formatted message.
Example:  

```c
void printMessage() {
    printf("This is a function with no return value.\n");
}
```

📌 Modify it to take user input and print a custom message.

### 5️⃣ Function Challenge: Calculator with Functions
✅ Rewrite your calculator program from Day 7 but use separate functions for:  
* Addition
* Subtraction
* Multiplication
* Division
* Getting user input

📌 Bonus Challenge: Add error handling for division by zero.

### 6️⃣ Debugging Exercise
I can provide buggy function code that you have to fix. Let me know if you want some debugging challenges! 🛠️

## Question to ChatGPT
```
Thank you for this. Regarding activity 5 from day 8. What is the parameter I 
should accept for a function that will be asking for, storing, and then 
outputting a string from the user. Also, what is the correct '%' symbol to use 
when I want to interpolate the inputted string using printf?
```
You're very welcome! Great question — when dealing with strings in C, you're really working with character arrays. Here's how to handle them in a function that asks for, stores, and prints a user-inputted string:

### ✅ 1. Function Parameter for a String
In C, you typically pass a string as a `char array` or a `char pointer`. For example:

```c
void getInput(char str[], int size);
```
or equivalently:

```c
void getInput(char *str, int size);
```
Both of these mean: “This function accepts a character array (string) and the size of that array.”

### ✅ 2. Format Specifier for `printf()`
To print a string using `printf()`, use:

```perl
%s
```
Example:
```c
printf("Hello, %s!\n", name);
```

### ✅ 3. Putting It All Together
Here’s a complete example that:  
* Uses a function to ask for input
* Stores it in a string (char array)
* Prints it back using %s

```c
#include <stdio.h>

void getInput(char str[], int size) {
    printf("Enter your name: ");
    fgets(str, size, stdin);  // safer than scanf for strings
}

int main() {
    char name[50];  // allocate space for the name
    getInput(name, 50);
    printf("Hello, %s", name);  // %s to interpolate the string

    return 0;
}
```
### 📝 Notes:
`fgets()` is generally preferred over `scanf("%s", ...)` because it handles spaces and avoids buffer overflow (with size limit).

`fgets()` includes the newline character if the input is short enough — you may want to strip it out if needed.

## Question to ChatGPT
```
Thanks for that. I am familiar with other programming languages. So I am 
familiar with the concept of scope. Regarding the last snippet of code you 
provided to me.  Since the `getInput` function is void, it doesn't return the 
str[].  I see that in the main function char name[50] is defined the `getIput` 
function call assigns the `name[50]` and the 50 as the second parameter. but I 
don't see that the `fgets` function directly assigns `char name[50]` directly to 
the user input. 

Does `fgets` assign the string. I guess what I am saying that I don't fully 
understand how `fgets` works. and how assignment is done... also that I don't 
fully understand how scope works in C. I am sure that these topics are 
discussed later on in this course, can you breifly discuss these topics so 
that I can better reason about this code?
```
Absolutely — you're asking great questions here, especially coming from a background in other programming languages. Let’s break down how fgets() works, how assignment works in this context, and how scope behaves in C.

## 🧠 How fgets() Works in C
```c
fgets(str, size, stdin);
```

✅ What's going on?  
* `str`: **A pointer to a character array** (i.e., a buffer where input will be stored).
* `size`: The **maximum number of characters to read**, including the null terminator `('\0')`.
* `stdin`: The input stream (standard input = the keyboard).

### 🔍 Does fgets() assign the string?
Yes. `fgets()` modifies the memory pointed to by `str`. Since arrays in C decay to pointers when passed to functions, changes made to `str` **inside the function affect the original memory in** `main()`.  

This works `without needing to return anything`, because you're passing a reference to the memory.

### 🧠 Think of it like this:
```c
char name[50];        // Allocate memory in main()
getInput(name, 50);   // Pass a pointer to that memory
// getInput() can now directly write into name[]
```

### 📦 How Assignment Works Here
```c
fgets(str, size, stdin);
```
* This function copies characters from user input into the memory pointed to by str.
* When you declare `char name[50];`, you're allocating space for 50 characters.
* That space is passed to `getInput()`, and `fgets()` **fills it in with what the user types**.

You don’t need to return `str` because the function **already has access** to the memory you passed in.

## 🔍 Understanding Scope in C
### 🧠 General Rule:
In C, **scope** works block by block — variables defined in a block `({ ... })` are local to that block.  

So:

```c
void greet() {
    char name[50];  // This only exists inside greet()
}

int main() {
    char name[50];  // This is a completely different 'name'
}
```

#### ⚠️ Important:  
* **Variables passed by value** (like `int`, `float`, etc.) are copied — changes inside a function **do not** affect the original.
* **Arrays and pointers**, however, are passed as **references** to memory — so if you modify them inside a function, the changes **do persist**.

### 🧠 TL;DR for Your Example
```c
void getInput(char str[], int size);
```
* `str[]` is a reference to memory allocated in `main()`.
* `fgets()` writes input into that memory.
* Even though the function is `void`, the `name[]` array in `main()` now contains the user’s input.
* You’re not returning anything because you're **modifying memory via a pointer**.

### Question to ChatGPT
```
Thank you for that, also regarding activity 5 from day 8: writing a function 
that accepts user input. when defining the parameters for a function, if the 
variables that the parameters will affect are defined outside the function 
block, how would I make references to them. From what was said above, I am 
assuming that I can refer to them with pointers, I just don't know how to define 
the parameters as pointers. And two,  how can a return multiple values from a 
function; what I mean to ask is that in other programming languages, I would 
normally pass a complex data structure, like an array, a list, a hash map, or 
some other data structure. I'm sure that these topics will be covered in the 
preceding lessons, but it would be helpful to get a brief primer on these topics 
to be able to successfully complete chapter 8's task.
```
### 🔹 1. Passing Variables by Reference (Using Pointers)
In C, when you want to allow a function to **modify a variable defined outside its own scope**, you **pass a pointer** to that variable.

🔧 Example: Passing by reference
```c
void updateValue(int *num) {
    *num = 42;  // Dereference the pointer to change the original value
}

int main() {
    int x = 0;
    updateValue(&x);  // Pass the address of x
    printf("x is now: %d\n", x);  // Outputs: x is now: 42
    return 0;
}
```

#### 🧠 Key Concepts:
* `int *num` → a pointer to an integer.
* `*num = 42` → dereference it to set the actual value.
* `&x` → the “address of” `x`, passed into the function.

This applies to strings, structs, arrays, etc.

### 🔹 2. Using Pointers for Strings (char arrays)
From earlier:

```c
void getInput(char *buffer, int size) {
    fgets(buffer, size, stdin);  // Fills the buffer passed from main
}
```
No need to return anything — the changes happen directly in the memory the pointer references.

### 🔹 3. Returning Multiple Values from a Function
In C, functions can return only one value, but you can simulate multiple return values in a few ways:

#### ✅ Method 1: Use Pointers as "Output Parameters"
```c
void calculate(int a, int b, int *sum, int *product) {
    *sum = a + b;
    *product = a * b;
}

int main() {
    int x = 3, y = 4;
    int add, mult;
    calculate(x, y, &add, &mult);
    printf("Sum: %d, Product: %d\n", add, mult);
    return 0;
}
```
* You're returning multiple values via output parameters (`int *sum`, `int *product`).
* Clean and efficient.

#### ✅ Method 2: Use Structs
If you want a cleaner way to group data, you can define a `struct`.

```c
typedef struct {
    int sum;
    int product;
} Result;

Result calculate(int a, int b) {
    Result r;
    r.sum = a + b;
    r.product = a * b;
    return r;
}

int main() {
    Result res = calculate(3, 4);
    printf("Sum: %d, Product: %d\n", res.sum, res.product);
    return 0;
}
```
* Structs give you a way to **package data** and return it like an object or dictionary in other languages.

#### ✅ Method 3: Use Arrays (for homogenous data)
If you're returning a list of values of the same type, you can return an array via a pointer, but this gets into dynamic memory (which we'll cover later). For now, stick with pointers and structs for “multiple returns.”

### 🔹 4. TL;DR: To Complete Day 8's Activity
* Use char `*` (or `char str[]`) to accept a string input in a function.
* Use int `*`, `float *`, etc., if you want to update scalar variables from within the function.
* Use `struct` if you want to return multiple named values.
* Use multiple pointer arguments if you want to output multiple values from a function without returning anything.
