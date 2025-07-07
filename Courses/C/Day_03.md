* [Table of contents](./index.md)  
* [Syllabus](./C-Syllabus.md)  
* [Day 2](./Day_02.md)  
* [Day 4](./Day_04.md)  

# The C Programming Language - Day 3: Data types, variables, and constants (int, float, char, const, #define)

ChatGPT Prompt: Okay,  I'm ready for day 3: Day 3: Data types, variables, and 
constants (int, float, char, const, #define). can you please print out a summary 
of what the second day entails? and then a set of activities that would help me 
learn the contents of this day in a more holistic way?

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

#### **Key Notes:**
* `%d` → Used for printing `int`.
* `%f` → Used for printing `float` (default prints 6 decimal places).
* `%c` → Used for printing `char`.
* `%s` -> used for printing `char[]`

### 2. Constants in C
Constants are values that **cannot change** after being defined. There are two main types:  
#### ✅ **Using `const` keyword (variable-based constant)**
```c
const float PI = 3.14159;  
```

#### ✅ **Using #define (preprocessor macro)**
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

#### **Key Differences:**
* `const` → **Type-safe**, follows variable scope.
* `#define` → **Replaces value at compile-time**, no data type.

#### Taking User input in C (Using `scanf`)
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

| Data Type          | Format Specifier | Description                                | Memory Size (x64)                                   | Limitations & Range                                                                                                   | Example                |
| :-------:          | :--------------: | :----------                                | :-------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------- | :------                |
| int                | %d               | Integer (decimal)                          | 4 bytes                                             | -2,147,483,648 to 2,147,483,647                                                                                       | `scanf("%d", &num);`   |
| unsigned int       | %u               | Unsigned integer (non-negative)            | 4 bytes                                             | 0 to 4,294,967,295                                                                                                    | `scanf("%u", &num);`   |
| short              | %hd              | Short integer                              | 2 bytes                                             | -32,768 to 32,767                                                                                                     | `scanf("%hd", &num);`  |
| unsigned short     | %hu              | Unsigned short integer                     | 2 bytes                                             | 0 to 65,535                                                                                                           | `scanf("%hu", &num);`  |
| long               | %ld              | Long integer                               | 8 bytes (Linux/macOS), 4 bytes (Windows)            | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 (8 bytes) or -2,147,483,648 to 2,147,483,647 (4 bytes)        | `scanf("%ld", &num);`  |
| unsigned long      | %lu              | Unsigned long integer                      | 8 bytes (Linux/macOS), 4 bytes (Windows)            | 0 to 18,446,744,073,709,551,615 (8 bytes) or 0 to 4,294,967,295 (4 bytes)                                             | `scanf("%lu", &num);`  |
| long long          | %lld             | Long long integer                          | 8 bytes                                             | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807                                                               | `scanf("%lld", &num);` |
| unsigned long long | %llu             | Unsigned long long integer                 | 8 bytes                                             | 0 to 18,446,744,073,709,551,615                                                                                       | `scanf("%llu", &num);` |
| float              | %f               | Floating-point number                      | 4 bytes                                             | Single-precision floating-point. Approximately 6-9 decimal digits of precision.                                       | `scanf("%f", &num);`   |
| double             | %lf              | Double-precision floating-point number     | 8 bytes                                             | Double-precision floating-point. Approximately 15-17 decimal digits of precision.                                     | `scanf("%lf", &num);`  |
| long double        | %Lf              | Extended precision floating-point number   | 10 or 16 bytes (compiler/platform dependent)        | Extended-precision floating-point. Higher precision than double.                                                      | `scanf("%Lf", &num);`  |
| char               | %c               | Single character                           | 1 byte                                              | -128 to 127 or 0 to 255 (compiler dependent).                                                                         | `scanf("%c", &ch);`    |
| char[] (string)    | %s               | String (reads a word, stops at whitespace) | 1 byte per character + 1 byte for null terminator   | The size is determined at compile time and is fixed.                                                                  | `scanf("%s", str);`    |
| size_t             | %zu              | Unsigned integer type for sizes            | 8 bytes                                             | Unsigned integer that can hold the maximum size of any object in memory. Same as unsigned long long.                  | `scanf("%zu", &size);` |
| ptrdiff_t          | %td              | Signed integer for pointer differences     | 8 bytes                                             | Signed integer that can hold the difference between two pointers. Same as long long.                                  | `scanf("%td", &diff);` [|](|)

#### **Notes on White space**  
There are instances, for example when scanf accepts a integer and then 
immediately accept a character, where the previous '\n' (ENTER key) will
still be in the input buffer.

To instruct the `scanf` function to ignore any whitespace left over in the
input buffer **prefix the input data type with a space**:
```
scanf(" %c", &operator);
```

#### **Explanation:**
* `printf("Enter your birth year: ");` -> Promts the user.
* `scanf("%d", &birthYear);` -> Reads the integer (`%d`) and stores it in `birthYear`.
* `&birthYear` -> **Address-of operator** is needed for input storage.

### **Hands-On Activities for Today**  
#### ✅ **Activity 1: Declare and Print Different Data Types**  
Modify the program to store:
* Your age (`int`)
* Your height in meters (`float`)
* Your first initial (char)  
  Then, print them using printf().

#### ✅ **Activity 2: Experiment with Constants**
* Create a constant using `const`.
* Create a constant using `#define`.
* Try changing a `const` variable after declaration—what happens?

#### ✅ **Activity 3: Format Floating-Point Numbers**  
* Modify the `%f` format to print 2 decimal places (`%.2f`).

#### ✅ Challenge Activity
* Write a program that asks for a **user’s birth year** (integer).
* Calculate and print their **age in 2025**.
* Modify the program to ask for **another future year** instead of 2024.
* Try using a **constant** (`#define CURRENT_YEAR 2025`) instead of hardcoding `2025`.
* Add **error handling**: What happens if the user enters a future birth year?
