* [Table of contents](./index.md)  
* [Syllabus](./C-Syllabus.md)  
* [Day 4](./Day_04.md)  
* [Day 6](./Day_06.md)  

# The C programming language - Day 5: Control flow (`if`, `else`, `switch`)

```
ChatGPT prompt:
Okay,  I'm ready for day 5: Control flow (if, else, switch)

Can you please print out a summary of what the five day entails? Afterwards, 
please generate a  set of activities that would help me learn the contents of 
this day in a more holistic way? 
```

## Day 5: Control Flow in C (if, else, switch)
Today, you’ll learn how C makes decisions using control flow statements. These 
allow your program to respond dynamically based on conditions.

🔹 Key Topics for Day 5  
1️⃣ `if` **Statement** – Executes code only if a condition is true.  
2️⃣ `if-else` **Statement** – Chooses between two paths.  
3️⃣ `else if` **Statement** – Handles multiple conditions.  
4️⃣ `switch` **Statement** – A cleaner alternative to `if-else` for multiple options.

### **1️⃣ The `if` Statement**  
The `if` statement executes a block of code only when the condition is true.

📌 Syntax:
```c
if (condition) {
    // Code executes if condition is true
}
```
📌 Example:
```c
#include <stdio.h>

int main() {
    int age = 20;

    if (age >= 18) {
        printf("You are an adult.\n");
    }

    return 0;
}
```
✅ If `age >= 18`, it prints `"You are an adult`."  
❌ If `age` is less than 18, nothing happens.

### **2️⃣ The if-else Statement**
If the `if` condition is false, the `else` block runs.

📌 Syntax:
```c
if (condition) {
    // Executes if condition is true
} else {
    // Executes if condition is false
}
```
📌 Example:
```c
#include <stdio.h>

int main() {
    int age = 16;

    if (age >= 18) {
        printf("You are an adult.\n");
    } else {
        printf("You are a minor.\n");
    }

    return 0;
}
```
✅ `"You are a minor."` will be printed.  

### 3️⃣ The `else if` Statement (Multiple Conditions)
Use `else if` to handle multiple conditions.

📌 Syntax:
```c
if (condition1) {
    // Executes if condition1 is true
} else if (condition2) {
    // Executes if condition2 is true
} else {
    // Executes if no conditions are true
}
```
📌 Example:

```c
#include <stdio.h>

int main() {
    int score = 75;

    if (score >= 90) {
        printf("Grade: A\n");
    } else if (score >= 80) {
        printf("Grade: B\n");
    } else if (score >= 70) {
        printf("Grade: C\n");
    } else {
        printf("Grade: F\n");
    }

    return 0;
}
```
✅ If `score = 75`, the output is `"Grade: C"`.  
✅ If `score = 92`, the output is `"Grade: A"`.

### **4️⃣ The `switch` Statement**
A `switch` statement is **useful when checking multiple values of a single variable**.

📌 Syntax:
```c
switch (variable) {
    case value1:
        // Code executes if variable == value1
        break;
    case value2:
        // Code executes if variable == value2
        break;
    default:
        // Executes if no cases match
}
```
📌 Example:
```c
#include <stdio.h>

int main() {
    int day = 3;

    switch (day) {
        case 1:
            printf("Monday\n");
            break;
        case 2:
            printf("Tuesday\n");
            break;
        case 3:
            printf("Wednesday\n");
            break;
        default:
            printf("Invalid day\n");
    }

    return 0;
}
```
✅ If `day = 3`, output is `"Wednesday"`.  
✅ If `day = 5`, output is `"Invalid day"`.  
🔹 **Break Statement**: Prevents fall-through (executing all cases below the matched one).  
🔹 **Default Case**: Runs if no case matches.

### 📌 Hands-On Activities for Day 5
✅ Activity 1: Number Sign Detector  
Write a program that:  
1️⃣ Takes an integer input from the user.  
2️⃣ Prints whether the number is positive, negative, or zero using `if-else`.  

📌 Hint:
```c
if (num > 0) {
    printf("Positive");
} else if (num < 0) {
    printf("Negative");
} else {
    printf("Zero");
}
```

### ✅ Activity 2: Even or Odd (Using `if-else`)
Write a program that:  
1️⃣ Asks the user for a number.  
2️⃣ Uses if-else to check if it's even or odd.  
3️⃣ Prints the result.  

### ✅ Activity 3: Grade Calculator (Using `else if`)
Modify the grade calculator program to:  
1️⃣ Accept a score from the user.  
2️⃣ Print the grade based on this scale:  

90+ → A

80-89 → B

70-79 → C

60-69 → D

Below 60 → F

📌 **Bonus**: Handle invalid scores (e.g., score > 100 or score < 0).

### ✅ Activity 4: Simple Calculator (Using `switch`)
Write a program that:
1️⃣ Asks the user for two numbers and an operator (`+`, `-`, `*`, `/`).  
2️⃣ Uses a `switch` statement to perform the calculation.  
3️⃣ Prints the result.  

📌 Example Input:

```yaml
Enter first number: 10
Enter an operator: +
Enter second number: 5
```
📌 Example Output:

```makefile
Result: 15
````
📌 Hint:

```c
switch (operator) {
    case '+':
        printf("Result: %d", a + b);
        break;
    case '-':
        printf("Result: %d", a - b);
        break;
    // Add other cases...
}
```

### ✅ Activity 5: Days of the Week (Using switch)
Write a program that:  
1️⃣ Asks the user for a number (1-7).  
2️⃣ Prints the day of the week (1 = Monday, 2 = Tuesday, etc.).  
3️⃣ Uses switch to handle the logic.

📌 **Bonus**: Handle invalid inputs (e.g., 8 or 0).

### 🎯 Challenge Activity
📌 Task: Login System

Ask the user to enter a username and password.

If the username is "admin" and password is "1234", print "Access Granted".

Otherwise, print "Access Denied".

Use if-else.

📌 Bonus: Allow up to three login attempts.

### 🚀 Recap & Next Steps  
Today, you learned:  
✅ if, if-else, and else if for decision-making  
✅ switch statements for multiple choices  
✅ How to use operators in conditions
