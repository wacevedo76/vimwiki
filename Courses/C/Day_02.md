* [Table of contents](./index.md)  
* [Syllabus](./C-Syllabus.md)  
* [Day 1](./Day_01.md)  
* [Day 3](./Day_03.md)  

# The C Programming Language - Day 2: Writing and Compiling a Basic C Program
## Entry Notes
ChatGPT Prompt:  
Okay,  I'm ready for day 2: Writing and compiling a basic C program (printf, main, return 0;)

can you please print out a summary of what the second day entails? and is this the best way to get the contents and activities for each day?

## 1. Understanding the Structure of a C Program
A basic C program consists of:
* `#include <stdio.h>` → Includes the standard I/O library.
* `main()` function → The entry point of the program.
* `printf()` function → Prints text to the console.
* `return 0;` → Indicates successful execution.

**Example Program (hello.c)**

```c
#include <stdio.h>  // Standard Input/Output Library

int main() {
    printf("Hello, World!\n");  // Print message to the console
    return 0;  // Exit with success
}
```
## 2. Compiling and Running the Program
**Steps to compile and run the program:**

```sh
gcc hello.c -o hello
./hello
```
**Output:**
```
Hello, World!
```
## 3. Breaking Down the Code
| Component                  | Explanation                                                    |
| :-----------------         | -----------                                                    |
| #include <stdio.h>         | Includes the Standard I/O Library (needed for `printf`).       |
| int main()                 | Defines the main function (program execution starts here).     |
| { ... }                    | Encloses the body of the function.                             |
| printf("Hello, World!\n"); | Prints "Hello, World!" and moves to the next line (\n).        |
| return 0;                  | Indicates successful execution (important for error handling). |

## 4. Modifying the Program
**Experiment by printing more text:**

```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    printf("Learning C programming is fun!\n");
    return 0;
}
```
Try removing `return 0;` and see if the program still works. (Hint: It’s optional in main() for modern compilers, but good practice.)

## 5. Understanding Escape Sequences
Escape sequences help format text.
**Example:**

```c
Copy
Edit
printf("Line1\nLine2\n");   // New line
printf("Tab\tSpace\n");     // Tab spacing
printf("Backslash: \\ \n"); // Print \
```
## Summary of Activities for Today
✅ Write a basic C program.  
✅ Compile and run it using gcc.  
✅ Modify the output to print multiple lines.  
✅ Experiment with escape sequences.  

Is This the Best Way to Learn?
This structured approach (daily summaries + practical exercises) is great because:

It builds progressively, ensuring you grasp fundamental concepts before moving forward.

Each day has hands-on practice, making learning active.

You can modify and experiment with the code to reinforce concepts.

