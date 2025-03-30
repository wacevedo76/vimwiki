Day 6: Loops in C (for, while, do-while)
Today, you’ll learn how to repeat actions in C using loops. Loops help reduce code repetition and make programs more efficient.

🔹 Key Topics for Day 6
1️⃣ for Loop – Best for when you know how many times to repeat an action.
2️⃣ while Loop – Runs while a condition is true.
3️⃣ do-while Loop – Runs at least once, then repeats while a condition is true.

1️⃣ The for Loop
A for loop is useful when you know how many times to loop.

📌 Syntax:

c
Copy
Edit
for (initialization; condition; increment/decrement) {
    // Code block to execute
}
📌 Example: Print numbers 1 to 5

c
Copy
Edit
#include <stdio.h>

int main() {
    for (int i = 1; i <= 5; i++) {
        printf("%d\n", i);
    }
    return 0;
}
✅ Output:

Copy
Edit
1
2
3
4
5
🔹 int i = 1; → Start from 1
🔹 i <= 5; → Continue while i is ≤ 5
🔹 i++ → Increase i after each loop

2️⃣ The while Loop
A while loop runs as long as a condition is true.

📌 Syntax:

c
Copy
Edit
while (condition) {
    // Code block to execute
}
📌 Example: Print numbers 1 to 5

c
Copy
Edit
#include <stdio.h>

int main() {
    int i = 1;
    while (i <= 5) {
        printf("%d\n", i);
        i++; // Increment manually
    }
    return 0;
}
✅ Same output as for loop.

🔹 When to use while? → If you don’t know how many times to loop.

3️⃣ The do-while Loop
A do-while loop runs at least once, even if the condition is false.

📌 Syntax:

c
Copy
Edit
do {
    // Code block to execute
} while (condition);
📌 Example:

c
Copy
Edit
#include <stdio.h>

int main() {
    int i = 1;
    do {
        printf("%d\n", i);
        i++;
    } while (i <= 5);
    return 0;
}
✅ Same output as previous loops.

🔹 Main difference: The condition is checked AFTER the first run.

📌 Example where do-while is useful:

c
Copy
Edit
#include <stdio.h>

int main() {
    int num;
    do {
        printf("Enter a positive number: ");
        scanf("%d", &num);
    } while (num <= 0); // Keeps asking until input is positive
    return 0;
}
✅ Ensures the user enters a valid number at least once.

📌 Hands-On Activities for Day 6
✅ Activity 1: Print Even Numbers (Using for)
Write a program that prints all even numbers from 2 to 20 using a for loop.

📌 Hint:

c
Copy
Edit
for (int i = 2; i <= 20; i += 2) {
    printf("%d ", i);
}
✅ Activity 2: Countdown Timer (Using while)
Write a program that counts down from 10 to 1, then prints "Blast off!" using a while loop.

📌 Hint:

c
Copy
Edit
int i = 10;
while (i > 0) {
    printf("%d\n", i);
    i--;
}
printf("Blast off!\n");
✅ Activity 3: Number Guesser (Using do-while)
Write a program that:
1️⃣ Generates a random number (1-10).
2️⃣ Asks the user to guess the number.
3️⃣ Keeps looping until the user guesses correctly.

📌 Hint: Use rand() function and do-while.

c
Copy
Edit
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    int secret, guess;
    srand(time(0));  // Seed random number
    secret = (rand() % 10) + 1;

    do {
        printf("Guess a number (1-10): ");
        scanf("%d", &guess);
    } while (guess != secret);

    printf("Correct! The number was %d.\n", secret);
    return 0;
}
✅ Activity 4: Factorial Calculator (Using for Loop)
Write a program that:
1️⃣ Asks the user for a number.
2️⃣ Calculates the factorial of that number using a for loop.

📌 Example:
Input: 5
Output: 5! = 120

📌 Hint:

c
Copy
Edit
int fact = 1;
for (int i = 1; i <= num; i++) {
    fact *= i;
}
✅ Activity 5: Multiplication Table (Using Nested for)
Write a program that prints a multiplication table (1-10).

📌 Example Output:

python-repl
Copy
Edit
1 x 1 = 1
1 x 2 = 2
...
10 x 10 = 100
📌 Hint:

c
Copy
Edit
for (int i = 1; i <= 10; i++) {
    for (int j = 1; j <= 10; j++) {
        printf("%d x %d = %d\n", i, j, i * j);
    }
}
🎯 Challenge Activity
📌 Fibonacci Series (Using while)
Write a program that prints the first 10 Fibonacci numbers.

📌 Example Output:

Copy
Edit
0 1 1 2 3 5 8 13 21 34
📌 Hint: The next number is the sum of the previous two numbers.

c
Copy
Edit
int a = 0, b = 1, next;
printf("%d %d ", a, b);
while (count < 10) {
    next = a + b;
    printf("%d ", next);
    a = b;
    b = next;
}
🚀 Recap & Next Steps
Today, you learned:
✅ for loops for definite iteration.
✅ while loops for indefinite iteration.
✅ do-while loops for at least one execution.

Would you like additional practice before moving to Day 7 (Functions & Modular Programming)? 🚀
