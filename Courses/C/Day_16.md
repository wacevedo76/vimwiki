* [Syllabus](./C-Syllabus.md)  
* [Table of contents](./index.md)  
* [Day 15](./Day_15.md)  
* [Day 17](./Day_17.md)  

# Day 16: Multi-dimensional arrays

## 🧭 1. Introduction
In C, **multi-dimensional arrays** allow you to represent data in grid or table-like formats. These structures are essential for handling matrices, image data, or any information organized by rows and columns. Mastering them helps you better understand both memory layout and advanced pointer arithmetic — concepts that will serve you throughout systems programming, numerical computing, and beyond.

## 📌 2. Summary
Today you’ll learn:
1. How to declare and initialize multi-dimensional arrays
2. How to access and modify elements using index notation
3. How C stores multi-dimensional arrays in memory (row-major order)
4. How to iterate through a multi-dimensional array using nested loops
5. How to pass multi-dimensional arrays to functions
6. The difference between fixed-size and variable-length arrays

## 🧠 3. Concise Explanations
| Concept                       | Description                                            |
| ----------------------------- | -------------------------------------------------      |
| Array Declaration             | Define a 2D array using int `matrix[rows][cols];`      |
| Accessing Elements            | Use syntax like `matrix[i][j]` for row `i`, column `j` |
| Memory Layout                 | C stores 2D arrays in row-major order                  |
| Iteration                     | Use nested loops to walk through rows and columns      |
| Passing Arrays to Functions   | Must specify column size: void f(int arr[][cols])      |
| Variable-Length Arrays (VLAs) | Arrays with size defined at runtime (C99 feature)      |

## 🔍 4. Detailed Explanations
### 🔸 1. Declaring and Initializing
```c
int matrix[3][4];  // 3 rows, 4 columns

int filled[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};
```
* First index = row
* Second index = column
* C ensures all elements are laid out in memory row-by-row

### 🔸 2. Accessing and Modifying Elements
```c
matrix[0][1] = 99;
printf("%d\n", matrix[0][1]);  // prints 99
```

### 🔸 3. Row-Major Memory Layout
C stores:

```c
int mat[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};
```
In memory as:

```css
[1][2][3][4][5][6]
```
You can flatten or reinterpret this with pointer arithmetic:

```c
*(*(mat + 1) + 2) == mat[1][2]  // value: 6
```

### 🔸 4. Iterating with Nested Loops
```c
for (int i = 0; i < 2; i++) {
    for (int j = 0; j < 3; j++) {
        printf("%d ", mat[i][j]);
    }
    printf("\n");
}
```

### 🔸 5. Passing to Functions
Because arrays decay to pointers, you must specify the column size:

```c
void printMatrix(int rows, int cols, int mat[][cols]) {
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            printf("%d ", mat[i][j]);
        }
        printf("\n");
    }
}
```

### 🔸 6. Variable-Length Arrays (C99+)
You can define array sizes at runtime:

```c
int rows = 3, cols = 4;
int mat[rows][cols];  // VLA

mat[0][0] = 42;
```

Note: VLAs are not supported in all compilers, but GCC supports them well.

## 🧪 5. Exercises
### 🟢 Easy
1. Matrix Initialization
    * Declare a 2x3 array and assign values using loops.
    * Print the array in matrix format.
2. Matrix Copy
    * Copy contents of one 2D array into another using nested loops.

### 🟡 Medium
3. Sum of All Elements
    * Write a function that returns the sum of all elements in a 2D array.
4. Find Max Element
    * Write a function that returns the maximum element and its location (row, col).

### 🔴 Hard
5. Transpose Matrix
    * Write a function to transpose a 3x2 array into a 2x3 array.
    * Challenge: Do it in-place for a square matrix (e.g. 3x3).
6. Flatten Matrix with Pointers
    * Write a function that flattens a 2D array into a 1D array using pointer arithmetic.

## 🔁 6. Recap and Next Steps
###📌 Today you learned:
* How to declare, access, and iterate over multi-dimensional arrays
* That C stores 2D arrays in row-major layout
* How to pass arrays to functions and use variable-length arrays
* How pointer arithmetic interacts with 2D memory structure

### 🚀 Up Next:
**Day 17: Strings in C**
* You’ll explore how character arrays work with null terminators
* Learn how strings are just arrays of characters with special handling
* Practice using <string.h> functions like strcpy, strlen, and strcmp
