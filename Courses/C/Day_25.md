* [Syllabus](./C-Syllabus.md)
* [Table of contents](./index.md)
* [Day 24](./Day_24.md)
* [Day 26](./Day_26.md)

# 🧠 Day 25: Structs with Pointers

## 1. 📝 Introduction
Welcome to Day 25! Today, we'll combine two of C's most powerful features: `structs` and `pointers`. Using pointers with structs is essential for efficient programming. It allows you to modify struct data directly without making expensive copies, dynamically allocate memory for complex data structures, and build foundational data structures like linked lists. This is a critical skill for any serious C programmer.

## 2. 📌 Summary
By the end of this lesson, you will understand how to:
*   Declare a pointer to a `struct`.
*   Access `struct` members using the arrow operator (`->`).
*   Pass `structs` to functions by reference (using pointers).
*   Dynamically allocate memory for a `struct` on the heap using `malloc()`.
*   Understand the relationship between `(*ptr).member` and `ptr->member`.

## 3. 🚀 Concise Explanations
*   **Pointer to Struct:** A variable that stores the memory address of a `struct` variable.
*   **Arrow Operator (`->`):** A shorthand syntax used to access a `struct`'s members through a pointer. It replaces the more cumbersome `(*pointer).member` notation.
*   **Pass by Reference:** Passing a pointer to a `struct` to a function. This allows the function to modify the original `struct` data, which is more memory-efficient than passing by value (copying).
*   **Dynamic Allocation:** Using `malloc()` to create a `struct` on the heap, which is necessary when the struct's lifetime must extend beyond the function in which it was created.

## 4. 🧠 Detailed Explanations

### ✅ Declaring and Using Pointers to Structs
First, let's see how to declare a pointer and assign it the address of a struct.

```c
#include <stdio.h>
#include <string.h>

// Define a simple struct for a Student
typedef struct {
    char name[50];
    int id;
} Student;

int main() {
    // Create a Student variable on the stack
    Student s1;
    strcpy(s1.name, "Alice");
    s1.id = 12345;

    // Declare a pointer to a Student
    Student *student_ptr;

    // Assign the address of s1 to the pointer
    student_ptr = &s1;

    // Accessing members using the pointer
    // The "arrow" operator -> is the preferred way
    printf("Name: %s\n", student_ptr->name);
    printf("ID: %d\n", student_ptr->id);

    // This is the equivalent, but more verbose, way
    printf("Name (verbose): %s\n", (*student_ptr).name);
    printf("ID (verbose): %d\n", (*student_ptr).id);

    return 0;
}
```
**Annotation:**
*   `Student *student_ptr;` declares a pointer that can hold the address of a `Student` struct.
*   `student_ptr = &s1;` stores the memory address of `s1` in `student_ptr`.
*   `student_ptr->name` is syntactic sugar for `(*student_ptr).name`. It first dereferences the pointer (`*student_ptr`) to get the struct itself, and then accesses the `name` member with the dot operator. The arrow operator is cleaner and universally preferred.

### ✅ Passing Structs to Functions by Reference (Pointer)
Passing large structs by value (making a copy) is inefficient. Passing a pointer is much faster as you only copy an address (typically 4 or 8 bytes).

```c
#include <stdio.h>
#include <string.h>

typedef struct {
    char name[50];
    int score;
} Player;

// This function takes a POINTER to a Player struct
void update_score(Player *p, int new_score) {
    // Modify the original struct's data directly
    p->score = new_score;
    strcpy(p->name, "Winner"); // We can change any member
}

int main() {
    Player p1 = {"Player 1", 0};

    printf("Before update: %s, Score: %d\n", p1.name, p1.score);

    // Pass the ADDRESS of p1 to the function
    update_score(&p1, 100);

    printf("After update: %s, Score: %d\n", p1.name, p1.score);

    return 0;
}
```
**Analogy: The Blueprint**
Passing a struct by value is like giving someone a photocopy of a blueprint. They can draw on it, but the original blueprint is unchanged. Passing by reference (pointer) is like giving them the location of the original blueprint. Any changes they make are on the master copy for everyone to see.

### ✅ Dynamic Allocation of Structs with `malloc()`
Sometimes you need a struct to exist beyond a single function's scope. For this, you allocate it on the heap.

```c
#include <stdio.h>
#include <stdlib.h> // Required for malloc() and free()
#include <string.h>

typedef struct {
    char model[50];
    int year;
} Car;

int main() {
    // Declare a pointer for the Car
    Car *my_car;

    // Allocate memory on the heap for one Car struct
    // sizeof(Car) ensures we get the correct number of bytes
    my_car = (Car *)malloc(sizeof(Car));

    // Always check if malloc was successful
    if (my_car == NULL) {
        perror("Failed to allocate memory");
        return 1;
    }

    // Use the arrow operator to set the members
    strcpy(my_car->model, "Tesla Model S");
    my_car->year = 2025;

    printf("My car: %s (%d)\n", my_car->model, my_car->year);

    // IMPORTANT: Free the allocated memory when done
    free(my_car);
    my_car = NULL; // Good practice to avoid dangling pointers

    return 0;
}
```
**Diagram: Stack vs. Heap Allocation**
```
      STACK                              HEAP
+-------------------+             +-----------------+
| main()            |             |                 |
|   +-----------+   |             |   +-----------+ |
|   | Car *my_car | --points to-->|   | Car struct| |
|   +-----------+   |             |   | model, year | |
|   (pointer)     |             |   +-----------+ |
+-------------------+             | (actual data)   |
                                  +-----------------+
```

## 5. 🧪 Exercises
### 🟢 Easy
1.  **Struct Pointer Basics:** Create a `struct` named `Point` with two integer members, `x` and `y`. In `main`, create an instance of `Point`, declare a pointer to it, and use the pointer and the arrow operator (`->`) to set and print the values of `x` and `y`.

### 🟡 Medium
2.  **Function Modification:** Write a function `void move_point(Point *p, int delta_x, int delta_y)` that takes a pointer to a `Point` struct and adds `delta_x` and `delta_y` to its `x` and `y` members, respectively. In `main`, create a `Point`, print its initial values, call `move_point`, and print the modified values to show it worked.

### 🔴 Hard
3.  **Dynamic Student Records:** Create a `Student` struct (with `name` and `id`). Write a program that asks the user how many students they want to enter. Dynamically allocate an array of `Student` structs on the heap using `malloc`. Loop through the array, asking the user for each student's name and ID, and store it in the allocated memory. Finally, loop through the array again and print all the student records. Don't forget to `free` the memory at the end!

## 6. ✅ Recap and Next Steps
### ✔️ What You Learned:
*   Pointers can store the addresses of structs.
*   The arrow operator (`->`) is the clean and standard way to access members via a pointer.
*   Passing struct pointers to functions is efficient and allows for direct modification of the original data.
*   `malloc()` is used to create structs on the heap for a longer lifetime, and `free()` must be called to prevent memory leaks.

### 🔜 Coming Up Next:
For Day 26, we will explore more advanced data structures concepts: **Unions and bit-fields**. These allow for even more fine-grained control over memory, which is critical in systems programming and embedded applications. Get ready to think about how data is represented at the bit level!

```