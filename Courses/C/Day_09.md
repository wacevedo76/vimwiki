* [Table of contents](./index.md)  
* [Syllabus](./C-Syllabus.md)  
* [Day 8](./Day_08.md)  
* [Day 10](./Day_10.md)  

# The C programming language - Day 9: Function parameters and return values

## Summary: What Day 9 Entails
Today, you’ll deepen your understanding of functions in C by learning:

1. **Function Parameters**
* How to pass values into a function
* Difference between:
    * Pass by value (copy of the variable)
    * Pass by reference (using pointers)

2. **Function Return Values**
* Returning data from a function using the `return` keyword
* Return types (`int`, `float`, `char`, `void`, etc.)
* Returning multiple values via pointers or structures

3. **Parameter Scope & Lifetime**
* Local variables vs global variables
* How parameter scope affects what you can do with variables inside and outside functions

## 🎯 Activities for Day 9 (Holistic Learning)
### 🔹 Activity 1: Basic Function with Return
Write a function `int square(int n)` that returns the square of a number.  
✅ Call it from `main()` and print the result.

### 🔹 Activity 2: Pass by Reference
Write a function `void swap(int *a, int *b)` that swaps two integers using pointers.  
✅ Call it and print before/after values in `main()`.

### 🔹 Activity 3: Returning Multiple Values
Create a function `void calculate(int a, int b, int *sum, int *diff)` that:
* Calculates sum and difference
* Stores results using pointer parameters

✅ Print values in `main()`.

### 🔹 Activity 4: User Input Function  
Write a function void `getUserInput(char *prompt, int *value)` that:
* Prompts the user with a custom message
* Reads input into a provided variable via pointer

#### 🔹 Challenge Activity: Mini Math Toolkit
Build a program that:
* Asks the user for two numbers
* Uses separate functions to:
    * Add, subtract, multiply, divide
* Returns or prints results clearly

### 💡 Stretch Goal: Struct + Function
* Define a `struct Result { int sum; int product; };`
* Write a function `struct Result compute(int a, int b);`
* Return both values in one object

## 🔹 1. Function Parameters
### ✅ What Are Function Parameters?
Parameters are **placeholders** used in a function definition that allow you to pass values into the function when it's called.

### 🧠 Key Concepts
* Syntax:

```c
void greet(char name[]) {
    printf("Hello, %s!\n", name);
}
```
* Types of Parameters:
    * Pass by Value (default): Copies the value.
    * Pass by Reference: Passes the memory address using a pointer.

### 🧪 Example: Pass by Value
```c
void addOne(int n) {
    n = n + 1;
    printf("Inside function: %d\n", n);
}

int main() {
    int num = 5;
    addOne(num);
    printf("Outside function: %d\n", num);  // Still 5
}
```
### 🧪 Example: Pass by Reference
```c
void addOne(int *n) {
    *n = *n + 1;
}

int main() {
    int num = 5;
    addOne(&num);
    printf("Updated: %d\n", num);  // Now 6
}
```
### 🧠 &var vs *var — What's the Difference?
| Symbol | Meaning                                                              | Use Case                                                                 |
| ------ | -------                                                              | --------                                                                 |
| &var   | "Address of var" — gives you a pointer to the variable               | Used when you want to pass the address to a function, or store a pointer |
| `*ptr` | "Dereference ptr" — gives you the value at the address stored in ptr | Used to access or modify the value the pointer points to                 |

#### 📦 Visual Analogy:
Think of memory like mailboxes.
Each variable lives in a box and has an address.

```c
int age = 30;
```
* `age` is the value inside the box (📦).
* `&age` is the address on the box (📮).
* `int *ptr = &age;` — the pointer stores the address.
* `*ptr` — opens the box and sees what's inside (30).

#### 🔧 Example:
```c
#include <stdio.h>

void modify(int *x) {
    *x = 99;  // change the value at the address x points to
}

int main() {
    int a = 10;
    modify(&a);  // pass the address of a
    printf("%d\n", a);  // prints 99
    return 0;
}
```
**Explanation:**
* `&a` gives the address of `a` 
* `*x` inside the function dereferences that address and changes the original variable

## 🔹 2. Function Return Values
### ✅ What Is a Return Value?
Functions can **return** a result to the part of the program that called them.

### 🧠 Key Concepts
* The return type must be declared:

```c
int square(int x) {
    return x * x;
}
```
* Use return to send back a value.
* Only one value can be returned directly.

### 🧪 Example: Returning a Value
```c
int doubleIt(int x) {
    return x * 2;
}

int main() {
    int result = doubleIt(4);
    printf("Result: %d\n", result);  // 8
}
```
### 🧪 Returning Multiple Values (via Pointers)
```c
void sumAndDiff(int a, int b, int *sum, int *diff) {
    *sum = a + b;
    *diff = a - b;
}
```
### 🧪 Returning a Struct (Optional Advanced Technique)
```c
struct Result {
    int sum;
    int product;
};

struct Result calculate(int x, int y) {
    struct Result r;
    r.sum = x + y;
    r.product = x * y;
    return r;
}
```

### Notes on `struct`
#### Question to ChatGPT
```
Quick question. so defining a struct is essentially defining a custom data type?
```

Yes, exactly! 🙌  

Defining a struct in C is creating your own custom data type — it's like saying, "I want a new type that groups together several pieces of related data."

##### ✅ Think of it like this:
Basic types: `int`, `float`, `char`

Your own type: `struct Person,` `struct Result,` etc.

##### 🔧 Example: Defining a Struct
```c
struct Person {
    char name[50];
    int age;
    float height;
};
```
Now, struct Person is a custom data type that you can use like this:

```c
struct Person p1;

strcpy(p1.name, "Alice");
p1.age = 30;
p1.height = 5.6;

printf("%s is %d years old and %.1f feet tall\n", p1.name, p1.age, p1.height);
```
##### 📝 Tip:
If you want to make it even easier to use (and avoid always typing struct), you can use a typedef:

```c
typedef struct {
    char name[50];
    int age;
} Person;

Person p2;
```
Now you can just use Person like any built-in type.


## 🔹 3. Parameter Scope & Lifetime
### ✅ What Is Scope?
Scope refers to `where a variable is accessible` within the program.

### 🧠 Types of Scope
| Scope Type         | Where It Exists                 | Accessibility                  |
| ----------         | ---------------                 | -------------                  |
| Local              | Inside a function or block      | Only in that block             |
| Function Parameter | Part of a function's definition | Only within that function      |
| Global             | Declared outside any function   | Accessible throughout the file |

###🧪 Example: Local Scope
```c
void myFunction() {
    int a = 5;  // local to myFunction
    printf("%d\n", a);
}
```
### 🧪 Example: Global Scope
```c
int count = 0;

void increment() {
    count++;
}
```
### 🔁 Lifetime of Variables
* Local variables: Exist only during function execution.
* Global/static variables: Exist for the program’s entire runtime.

### ✅ Quick Summary
| Concept             | Description                                      |
| -------             | -----------                                      |
| Function Parameters | Allow input to functions (by value or reference) |
| Return Values       | Output results from functions using return       |
| Scope & Lifetime    | Define visibility and lifespan of variables      |
