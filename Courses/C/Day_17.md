* [Syllabus](./C-Syllabus.md)  
* [Table of contents](./index.md)  
* [Day 16](./Day_16.md)  
* [Day 18](./Day_18.md)  

# Day 17: Strings (char arrays, gets, puts, strcpy, strlen)

ChatGPT Prompt:
```
okay,  I’m ready for the next lesson: "Day 17: Strings (char arrays, gets, puts, strcpy, strlen)" Please generate a tutorial
using the following format and preferences:

1. **Introduction**  
   - Briefly introduce the topic and its importance in C programming.

2. **Summary**  
   - List the key concepts or learning objectives for this lesson.

3. **Concise Explanations**  
   - Provide short, clear explanations for each concept listed in the summary.

4. **Detailed Explanations**  
   - Offer intermideate-friendly, in-depth explanations using:
     - Annotated C code examples compatible with GCC 15.1.1 on Linux.
     - Analogies or metaphors to make abstract ideas more relatable.
     - Diagrams or ASCII-style visuals where helpful.

5. **Exercises**  
   - Present a series of progressively challenging exercises labeled with difficulty (Easy, Medium, Hard).
   - Include clear instructions and any background needed to complete them.
   - *Do not include solutions unless requested.*

6. **Recap and Next Steps**  
   - Summarize what I’ve learned.
   - Suggest what I should prepare for or review next in
```

## 📘 1. Introduction
In C, strings are **null-terminated character arrays** — that means a string is a sequence of characters ending with the special character `'\0'`. Unlike in higher-level languages, C does not have a dedicated string type, so understanding how strings work under the hood is essential for managing memory, working with user input, and performing text-based operations.

## 📋 2. Summary
Today you’ll learn:
1. How strings are represented using `char` arrays
2. How to declare and initialize strings
3. How to use standard functions: `gets,` `puts`, `strcpy`, `strlen`
4. How null terminators (`'\0'`) mark the end of strings
5. Common pitfalls with strings (like buffer overflows)
6. Safer alternatives (`fgets` vs `gets`, bounds checking)

## ✍️ 3. Concise Explanations
| Concept                | Description                                                     |
| --------------------   | --------------------------------------------------------------- |
| `char` arrays          | Arrays of characters representing strings                       |
| Null terminator `'\0'` | Marks the end of a string in memory                             |
| `gets` and `puts`      | Basic (but outdated/unsafe) functions for input/output          |
| `strcpy(dest, src)`    | Copies `src` into `dest`, including the null terminator         |
| strlen(str)            | Returns the length of the string (not including `'\0`)          |
| Buffer overflow        | Occurs when writing past the end of a string’s allocated memory |
| Safer functions        | `fgets`, `strncpy` are safer alternatives to `gets`, `strcpy`   |

## 🔍 4. Detailed Explanations
### 🔸 1. `char` Arrays and Initialization
```c
char name1[] = "William";
char name2[10] = "Anna";
```
* "William" is stored as:

```css
['W', 'i', 'l', 'l', 'i', 'a', 'm', '\0']
```
* The \0 is automatically appended when using string literals.

### 🔸 2. `gets` and `puts`
```c
char name[50];
gets(name);         // ❌ UNSAFE: can overflow buffer
puts(name);         // ✅ Prints string followed by newline
```
⚠️ gets() was removed from the C standard (C11). Use fgets() instead:

```c
fgets(name, sizeof(name), stdin);  // ✅ Safe alternative
```

### 🔸 3. `strcpy(dest, src)` — Copying Strings
```c
char src[] = "hello";
char dest[10];
strcpy(dest, src);   // dest now holds "hello"
```
⚠️ dest must be large enough. Otherwise → overflow → crash or vulnerability.

### 🔸 4. `strlen(str)` — String Length
```c
char str[] = "hello";
int len = strlen(str);  // returns 5 (doesn't count '\0')
```
Useful when sizing buffers, trimming input, etc.

### 🔸 5. `xtrcspn` - Removing trailing newline characters
```c
textinput[strcspn(textinput, "\n")] = '\0';
```
* finds the first newline character and replaces it with '\0'.

### 🔸 6. Common Pitfall: Buffer Overflow
```c
char tiny[5];
strcpy(tiny, "Overflow");  // ❌ too big → writes past array boundary
```
This can corrupt memory and cause bugs or security issues.

### 🔸 7. Safer Alternatives
| Unsafe     | Safer Alternative                      |
| --------   | -----------------------------------    |
| `gets()`   | `fgets()`                              |
| `strcpy()` | `strncpy()` or manual bounds checking  |

### 🧠 ASCII Diagram: String in Memory
```c
char s[] = "Hi";

s[0] → 'H'
s[1] → 'i'
s[2] → '\0'
```

## 🧪 5. Exercises
### 🟢 Easy
1. Declare a string and print it
    * Use char array and puts.
2. String length
    * Write a program that reads a string from input and prints its length using `strlen`.

### 🟡 Medium
3. Copy two strings
    * Read one string, copy it into another array using strcpy, and print both.
4. Safe input with fgets()
    * Read a sentence with spaces safely and print it.

### 🔴 Hard
5. Manual string copy
    * Write your own my_strcpy(dest, src) function using a loop.
6. Manual string length
    * Write a function my_strlen that mimics strlen by counting until '\0'.

## 🧾 6. Recap and Next Steps
### ✅ Today You Learned:
* How strings are represented as char arrays
* How to read and write strings using standard library functions
* Why '\0' is essential to all string operations
* The dangers of buffer overflows
* Safer ways to handle string input/output

### 🔜 Coming Up:
**Day 18: String Manipulation Functions**
* strcmp, strcat, strchr, strstr
* How to search and compare strings
* Build your own string utilities
