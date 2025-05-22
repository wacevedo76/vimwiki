* [Syllabus](./C-Syllabus.md)  
* [Table of contents](./index.md)  
* [Day 17](./Day_1r.md)  
* [Day 19](./Day_19.md)  

# Day 18: String manipulation functions (strcat, strcmp, strncpy)

Great! Welcome to **Day 18: String Manipulation Functions** — one of the most useful and hands-on areas in C string handling. By learning to combine, compare, and safely manage strings, you're moving from string basics to practical, everyday tools used in real-world applications like parsers, file handling, and user input validation.

## 📘 1. Introduction
C strings are just arrays of characters, but the standard library provides powerful tools for manipulating them. Today’s lesson focuses on concatenating, comparing, and copying strings safely, and learning to avoid common bugs like buffer overflows.

These operations are part of `<string.h>`, and mastering them helps you:
* Build longer strings from parts
* Check for matches between user input and stored strings
* Copy and store data securely

## 📋 2. Summary
Today’s key functions:
1. `strcat()` — concatenate one string onto another
2. `strcmp()` — compare two strings lexicographically
3. `strncpy()` — safely copy part or all of one string into another
4. Common pitfalls (missing '\0', overlapping memory, overflows)
5. Writing your own simple versions of these for practice

## ✍️ 3. Concise Explanations
| Function      | What it does                                               |
| `strcat()`    | Appends one string to the end of another                   |
| `strcmp()`    | Returns 0 if equal, <0 if left < right, >0 if left > right |
| `strncpy()`   | Safely copies `n` characters from source to dest           |
| `'\0'` issues | All functions rely on proper null-termination              |

## 🔍 4. Detailed Explanations
### 🔸 `strcat(dest, src)` — Concatenate Strings
```c
char a[20] = "Hello, ";
char b[] = "world!";
strcat(a, b);
printf("%s\n", a);  // → Hello, world!
```
* Appends contents of `b` to the end of `a`
* `a` must be large enough to hold both strings + `'\0'`

⚠️ Common bug: forgetting to allocate enough space in `dest`

### 🔸 `strcmp(a, b)` — Compare Two Strings
```c
strcmp("cat", "dog")   → negative (because 'c' < 'd')
strcmp("dog", "cat")   → positive
strcmp("apple", "apple") → 0 (strings are equal)
```

* Returns:
    * `0` if equal
    * `< 0` if `a < b`
    * `> 0` if `a > b` (lexicographically)

Case-sensitive: `"Cat"` ≠ `"cat"`

### 🔸 `strncpy(dest, src, n)` — Copy with Limit
```c
char src[] = "hello";
char dest[10];
strncpy(dest, src, 3);
dest[3] = '\0';  // manually null-terminate
```
* Copies at most `n` characters
* If `src` is shorter than `n`, fills with `\0`
* Safer than `strcpy()` but doesn’t guarantee null-termination if `src` is longer than `n`

### 🧠 Analogy: String Handling as Boxes
* Imagine each `char` is a box labeled with a letter.
* `strcat()` = tape two rows of boxes together (with care).
* `strcmp()` = sort alphabetically and check box by box.
* `strncpy()` = scoop up the first N boxes, carefully stopping at a wall.

### 🧠 ASCII Diagram: strcat()
```yaml
Before:
dest:  [H][e][l][l][o][,][ ][\0] . . . . .
src :  [w][o][r][l][d][!][\0]

After strcat(dest, src):
dest:  [H][e][l][l][o][,][ ][w][o][r][l][d][!][\0]
```

## 🧪 5. Exercises
### 🟢 Easy
1. Concatenate "Good" and "Morning" using `strcat()` into a buffer.
2. Compare two strings entered by the user using `strcmp()` and report equality or lexicographic order.

### 🟡 Medium
3. Write a function `my_strcmp()` that mimics `strcmp()` using a `while` loop.
4. Use `strncpy()` to copy only the first 5 characters of a sentence into a new buffer and print both.

### 🔴 Hard
5. Build a sentence by concatenating three strings safely using `strncat()`.
6. Write a `safe_strcat()` function that:
    * Checks if the combined length fits in `dest`
    * Appends only what fits
    * Guarantees null-termination

## 🔚 6. Recap and Next Steps
### ✅ Today You Learned:
* How to combine, compare, and copy strings with C library functions
* The difference between safe and unsafe versions
* How to write your own simple `strcmp()`-like logic
* Why null-termination is essential

🔜 Up Next:
Day 19: Command-Line Arguments and Environment Variables
* How to read argc and argv[]
* Pass input to your program from the terminal
* Read environment variables dynamically
