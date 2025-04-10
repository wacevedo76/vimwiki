* [Table of contents](./index.md)  
* [Syllabus](./C-Syllabus.md)  
* [Day 2](./Day_02.md)  
* [Day 4](./Day_04.md)  

# The C Programming Language - Day 3: Data types, variables, and constants (int, float, char, const, #define)

ChatGPT Prompt: Okay,  I'm ready for day 3: Day 3: Data types, variables, and constants (int, float, char, const, #define). 

can you please print out a summary of what the second day entails? and then a set of activities that would help me learn the contents of this day in a more holistic way?

## Day 3: Data Types, Variables, and Constants
Today, you’ll learn how C stores and manipulates numbers, characters, and constants.

### 1. Basic Data Types in C
| Type           | Keyword       | Description               | Example           |
| ----           | :-----:       | -----------               | -------           |
| Integer        | int           | Stores whole numbers      | int age = 25;     |
| Floating Point | float, double | Stores decimal numbers    | float pi = 3.14;  |
| Character      | char          | Stores a single character | char grade = 'A'; |

** Example Code:**

```c
#include <stdio.h>

int main() {
    int age = 30;
    float pi = 3.1415;
    char grade = 'A';

    printf("Age: %d\n", age);
    printf("Pi: %f\n", pi);
    printf("Grade: %c\n", grade);
    return 0;
}
```
**Key Notes:**
* `%d` → Used for printing `int`.
* `%f` → Used for printing `float` (default prints 6 decimal places).
* `%c` → Used for printing `char`.

### 2. Constants in C
Constants are values that **cannot change** after being defined. There are two main types:  
✅ **Using `const` keyword (variable-based constant)**
```c
const float PI = 3.14159;  
```
✅ **Using #define (preprocessor macro)**
```c
#define PI 3.14159
```
** Example Code:

```c
#include <stdio.h>

#define PI 3.14159  // Macro constant

int main() {
    const int daysInWeek = 7;  // Immutable variable

    printf("Days in a week: %d\n", daysInWeek);
    printf("Value of Pi: %f\n", PI);
    return 0;
}
```
**Key Differences:**

* `const` → **Type-safe**, follows variable scope.

* `#define` → **Replaces value at compile-time**, no data type.

#### Taking User InPut in C (Using `scanf`)
The `scanf` function is used to take input from the user.
* It requires **format specifiers** (like "%d" for integers).
* The `&` **(address-of) operator** is used for variable input (except for `char[]`).

**Example: Taking an Integer Input**
```c
#include <stdio.h>

int main() {
  int birthYear;
  
  printf("Enter your birth year: ");
  scanf("%d", &birthYear);  // Taking integer input
  
  printf("You entered: %d\n", birthYear)
  return 0;
}
```
#### Common data types that scanf can accept

Here’s a table of the common data types scanf() can accept, along with their corresponding format specifiers:

| Data Type          | Format Specifier | Description                                | Example                |
| :-------:          | :--------------: | :----------                                | :------                |
| int                | %d               | Integer (decimal)                          | `scanf("%d", &num);`   |
| unsigned in        | %u               | Unsigned integer (non-negative)            | `scanf("%u", &num);`   |
| short              | %hd              | Short integer                              | `scanf("%hd", &num);`  |
| unsigned short     | %hu              | Unsigned short integer                     | `scanf("%hu", &num);`  |
| long               | %ld              | Long integer                               | `scanf("%ld", &num);`  |
| unsigned long      | %lu              | Unsigned long integer                      | `scanf("%lu", &num);`  |
| long long          | %lld             | Long long integer                          | `scanf("%lld", &num);` |
| unsigned long long | %llu             | Unsigned long long integer                 | `scanf("%llu", &num);` |
| float              | %f               | Floating-point number                      | `scanf("%f", &num);`   |
| double             | %lf              | Double-precision floating-point number     | `scanf("%lf", &num);`  |
| long double        | %Lf              | Extended precision floating-point number   | `scanf("%Lf", &num);`  |
| char               | %c               | Single character                           | `scanf("%c", &ch);`    |
| char[] (string)    | %s               | String (reads a word, stops at whitespace) | `scanf("%s", str);`    |
| size_t             | %zu              | Unsigned integer type for sizes            | `scanf("%zu", &size);` |
| ptrdiff_t          | %td              | Signed integer for pointer differences     | `scanf("%td", &diff);` [|](|)

**Notes on White space**  
There are instances, for example when scanf accepts a interger and then 
immediatly accept a character, where the previousl '\n' (ENTER key) will
still be in the input buffer.

To instruct the `scanf` function to ignore any whitespace left over in the
input buffer **prefix the input data type with a space**:
```
scanf(" %c", &operator);
```

**Explanation:**
* `printf("Enter your birth year: ");` -> Promts the user.
* `scanf("%d", &birthYear);` -> Reads the integer (`%d`) and stores it in `birthYear`.
* `&birthYear` -> **Address-of operator** is needed for input storage.

**Hands-On Activities for Today**  
✅ **Activity 1: Declare and Print Different Data Types**  
Modify the program to store:
* Your age (`int`)
* Your height in meters (`float`)
* Your first initial (char)  
  Then, print them using printf().

✅ **Activity 2: Experiment with Constants**
* Create a constant using `const`.
* Create a constant using `#define`.
* Try changing a `const` variable after declaration—what happens?

✅ **Activity 3: Format Floating-Point Numbers**  
* Modify the `%f` format to print 2 decimal places (`%.2f`).

✅ Challenge Activity
* Write a program that asks for a **user’s birth year** (integer).
* Calculate and print their **age in 2025**.
* Modify the program to ask for **another future year** instead of 2024.
* Try using a **constant** (`#define CURRENT_YEAR 2025`) instead of hardcoding `2025`.
* Add **error handling**: What happens if the user enters a future birth year?
