* [table of contents](./index.md)  
* [Syllabus](./C-Syllabus.md)  
* [Day 5](./Day_05.md)

# The C Programming Language - Day 4: Operators and Expressions in C
```
ChatGPT Prompt:  
Okay,  I'm ready for day 4: Operators and expressions `(+, -, *, /, %, ++, --)`.

Can you please print out a summary of what the fourth day entails? and then a set 
of activities that would help me learn the contents of this day in a more holistic 
way? Today, you’ll learn how to perform arithmetic operations in C and how 
expressions work.
```

Today, you’ll learn how to perform arithmetic operations in C and how expressions work.

## Key Topics for Day 4
1. Arithmetic Operators: Perform basic calculations in C.
2. Increment (++) and Decrement (--) Operators: Modify values efficiently.
3. Operator Precedence: Understand how C evaluates expressions.

### Arithmetic Operators in C
C supports the following arithmetic operators:

| Operator       | Symbol | Example | Description                                            |
| :------:       | :----: | :-----: | -----------                                            |
| Addition       | `+`    | `a + b` | Adds two numbers                                       |
| Subtraction    | `-`    | `a - b` | Subtracts two numbers                                  |
| Multiplication | `*`    | `a * b` | Multiplies two numbers                                 |
| Division       | `/`    | `a / b` | Divides two numbers (integer division if both are int) |
| Modulus        | `%`    | `a % b` | Remainder of division (only for integers)              |

**Integer vs. Floating-Point Division**
* If both numbers are int, division truncates (removes) decimal places.
* If at least one number is float or double, division preserves decimals.

**Example:**

```c
#include <stdio.h>

int main() {
    int a = 10, b = 3;
    float x = 10.0, y = 3.0;

    printf("Integer Division: %d\n", a / b);  // Output: 3
    printf("Floating-Point Division: %.2f\n", x / y);  // Output: 3.33

    return 0;
}
```
:## 2. Increment (++) and Decrement (-\-) Operators
These are shorthand for increasing or decreasing a value by 1.

| Operator  | Symbol | Example         | Equivalent To |
| --------- | :----: | :--------:      | :-----------: |
| Increment | `++`   | `a++` or `++a`  | `a = a + 1`   |
| Decrement | `--`   | `a--` or `--a`  | `a = a - 1`   |

**Prefix (`++a, --a`) vs. Postfix (`a++, a--`)**

* **Prefix** (++a, --a) → Increments **before** using the variable.

* **Postfix** (`a++, a--`) → Increments **after** using the variable.

**Example:**

```c
#include <stdio.h>

int main() {
    int a = 5, b = 5;

    printf("Prefix Increment: %d\n", ++a);  // a becomes 6, then prints 6
    printf("Postfix Increment: %d\n", b++); // Prints 5, then b becomes 6

    printf("New value of b: %d\n", b);  // Now b is 6
    return 0;
}
```

### 3. Operator Precedence (Order of Execution)
Like in math, some operations happen before others.

| Precedence | Operators         |
| ---------- | :---------------: |
| Highest    | `()`, `++`, `--` |
| High       | `*`, `/`, `%`     |
| Medium     | `+`, `-`          |
| Lowest     | `=` (assignment)  |

**Example:**

```c
int result = 5 + 2 * 3; // result = 5 + (2 * 3) = 11
```
To **force a different order**, use parentheses:

```c
int result = (5 + 2) * 3; // result = 7 * 3 = 21
```

### Activities for Day 4  
✅ Activity 1: Basic Arithmetic Operations  
Write a program that:
1. Declares two integer variables (a, b).
2. Performs all arithmetic operations (`+`, `-`, `*`, `/`, `%`).
3. Prints the results.

✅ Activity 2: Increment & Decrement  
Write a program that:  
1. Declares an integer variable `x = 10`.
2. Uses `x++` and `++x`, printing `x` before and after each operation.
3. Uses `x--` and `--x`, printing `x` before and after each operation.

**Expected Output Example:**

```yaml
Initial x: 10
Postfix Increment: 10
Value after: 11
Prefix Increment: 12
Value after: 12
```

✅ Activity 3: Even or Odd? (Using `%`)  
Write a program that:
1. Asks the user for an integer.
2. Uses the modulus operator (%) to determine if it's even or odd.
3. Prints the result.

**Hint:**

```c
if (num % 2 == 0) {
    printf("Even");
} else {
    printf("Odd");
}
```

✅ Activity 4: Custom Expression Calculator
Write a program that:
1. Takes three user inputs (numbers).
2. Computes the following expression:

`result=(num1+num2)∗num3/2`

3. Prints the result.

**Bonus**: Modify the program to handle floating-point values (float instead of int).
