* [Syllabus](./C-Syllabus.md)  
* [Table of contents](./index.md)  
* [Day 20](./Day_20.md)  
* [Day 22](./Day_22.md)  

# Day 21: Mini-project: Simple text-based menu program


##1. Introduction
Text-based menu programs are one of the best beginner-friendly ways to simulate real applications — like system tools, command-line utilities, or small games. They teach:
* Control flow
* Input validation
* Function modularity
* Basic data management

You’ll write a simple interactive program where users can choose from a set of actions using a numbered menu.

## 2. Summary
Today you’ll learn to:
  1. Display a clear, repeatable menu using printf()
  2. Take and validate user input using scanf() / fgets()
  3. Use a switch or if/else structure to handle menu choices
  4. Organize code into functions for each action
  5. Use loops to keep the program running until the user exits

## 3. Concise Explanations
Concept	Description
Menu display	Show a list of options the user can choose from
Input capture	Read user choices and validate them
Switch/if-else	Determine which action to take based on user input
Function modularity	Split actions into reusable, well-named functions
Looping	Keep showing the menu until the user exits (e.g., enters 0 or q)

## 4. Detailed Explanations
### 🔸 Menu Display
```c
void showMenu() {
    printf("\n=== Main Menu ===\n");
    printf("1. Greet user\n");
    printf("2. Add two numbers\n");
    printf("3. Show program info\n");
    printf("0. Exit\n");
    printf("Enter your choice: ");
}
```
A simple function to encapsulate the menu. You’ll call this every loop iteration.

### 🔸 Capturing Input Safely
```c
int choice;
scanf("%d", &choice);
```
Optional: wrap in a loop to reject invalid (non-integer or out-of-range) inputs.

### 🔸 Using switch
```c
switch (choice) {
    case 1: greetUser(); break;
    case 2: addNumbers(); break;
    case 3: showInfo(); break;
    case 0: printf("Goodbye!\n"); break;
    default: printf("Invalid option.\n");
}
```
### 🔸 Using Functions for Each Action
```c
void greetUser() {
    char name[50];
    printf("Enter your name: ");
    scanf("%s", name);
    printf("Hello, %s!\n", name);
}
```
You’ll write a separate function for each task the menu can perform.

### 🔄 Looping Until Exit
```c
int running = 1;
while (running) {
    showMenu();
    scanf("%d", &choice);

    switch (choice) {
        case 0: running = 0; break;
        ...
    }
}
```
This keeps the program interactive.

### 🧠 Metaphor: Restaurant Menu
  * The screen is your “waiter”
  * The numbered options are the “menu items”
  * Your input selects what to “serve” (which function gets called)

### 🔠 ASCII Diagram (Simple Flow)
```less
[showMenu()]
     |
  [scanf()]
     |
  [switch]
   / |  \
[1][2]...[0]
 |  |     |
[greet][add][exit]
```

## 5. Exercises
### 🟢 Easy
1. Create a static menu with 3 options and use switch to print basic messages.
2. Write a function void sayHello() and call it when the user selects option 1.

### 🟡 Medium
3. Add a menu option to add two integers entered by the user.
4. Add input validation to reject non-integer input and prompt again.

### 🔴 Hard
5. Create a menu-driven to-do list using an array of strings.
6. Add an “admin mode” (password-protected) to show a hidden menu.

## 6. Recap and Next Steps
### ✅ Today You Practiced:
  * Designing a menu system
  * Controlling flow using switch and while
  * Creating modular, functional C programs
  * Validating and using user input

### 🔜 Next Step:
**Day 22: Dynamic Memory Allocation (`malloc`, `calloc`, `realloc`, `free`)**
You’ll move from fixed-size arrays to memory that grows at runtime — opening up powerful, flexible programming strategies.

