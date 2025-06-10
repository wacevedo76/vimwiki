* [Syllabus](./C-Syllabus.md)  
* [Table of contents](./index.md)  
* [Day 23](./Day_23.md)  
* [Day 25](./Day_25.md)  

# 🧠 Day 24: Introduction to `struct` and `typedef` in C

## 1. 📝 Introduction
In C programming, structures (`struct`) allow you to group variables of different types under a single name — essentially creating custom data types. This is vital for organizing complex data, building real-world applications like address books, to-do lists, and game states. Combined with `typedef`, you can create cleaner, more readable code by giving new names to your custom types.

## 2. 📌 Summary
Today you’ll learn to:
* Define and use `struct`.
* Access and modify `struct` members.
* Pass `struct` to functions.
* Use `typedef` to simplify type declarations.
* Combine `struct` and `typedef`.

## 3. 🚀 Concise Explanations
* `struct`: A user-defined data type that groups variables (members) of different types.
* Dot Operator (`.`): Used to access members of a `struct` variable.
* Arrow Operator (`->`): Used to access members through a pointer to a `struct`
* `typedef`: Defines a new name (alias) for an existing type, useful for cleaner syntax.
* Combining `struct` + `typedef`: Reduces verbosity and enhances readability.

## 4. 🧠 Detailed Explanations
### ✅ Declaring and Using a `struct`
```c
#include <stdio.h>

struct Person {
    char name[50];
    int age;
    float height;
};

int main() {
    struct Person john = {"John Doe", 30, 1.75};

    printf("Name: %s\n", john.name);
    printf("Age: %d\n", john.age);
    printf("Height: %.2f m\n", john.height);

    return 0;
}
```

### ✅ Accessing Members via Pointer (`->`)
```c
struct Person *ptr = &john;
printf("Name via pointer: %s\n", ptr->name); // Same as (*ptr).name
```

### ✅ Using `typedef` with `struct`
```c
typedef struct {
    char title[100];
    int completed;
} Task;

Task t1 = {"Finish C lesson", 0};
```
Now you can just use `Task` instead of `struct Task`

### 🧠 Metaphor: `Structs` as "Folders"
Think of a struct as a folder:
* The folder name is the struct variable.
* Inside the folder are documents of different types (int, float, char[]).
* You can pass the whole folder or make copies of it — but it’s still one unit.

### 🗂 Diagram: Struct Memory Layout (Simplified)
```arduino
struct Person {
   char name[50];   // Bytes 0–49
   int age;         // Bytes 50–53
   float height;    // Bytes 54–57
}
```

## 5. 🧪 Exercises
### 🟢 Easy
1. Create a struct named Book with fields: title (char[100]), author (char[50]), and pages (int). Print the values.
2. Write a function void printBook(Book b) that prints its contents.

### 🟡 Medium
3. Create an array of 5 Book structs. Prompt the user to enter values for each.
4. Write a function that searches for a Book by title and returns its index.

### 🔴 Hard
5. Create a `ToDoItem` struct with:
    * `char title[100]`
    * `char created_at[30]`
    * `int completed`

  Write a menu-driven program to:
    * Add new items
    * Mark items as completed
    * Display all items
    * Save/load to/from a file

## 6. ✅ Recap and Next Steps
### ✔️ What You Learned:
* `struct` lets you define custom data structures.
* Members are accessed with `.` or `->`.
* `typedef` simplifies type names.
* You can build real-world objects with `struct,` like tasks or books.

### 🔜 Coming Up Next:
* For Day 25, you’ll learn about structs and functions in more detail — including:
* Passing structs by reference vs value.
* Returning structs from functions.
* Nesting structs.

