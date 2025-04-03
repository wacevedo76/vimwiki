[table of contents](./index.md)
[Syllabus](./C-Syllabus.md)

# 📌 Day 7: Simple Exercises (Basic Calculator, Number Guessing Game)
```
Okay, I'm ready for Day 7: Simple exercises (basic calculator, number guessing
game) 

Can you please print out a  summary of what day seven entails? Afterwards,
please generate as set of activities that would help me learn the contents of
day seven in a more holistic way?
```
## 🔹 Summary of Day 7
Today, you’ll apply what you’ve learned over the past six days by building two small projects:

1. A Basic Calculator – A simple program that takes user input and performs arithmetic operations.
2. A Number Guessing Game – A game where the user tries to guess a randomly generated number.

These exercises will reinforce your understanding of:

* User input handling (`scanf`)
* Control flow (`if-else`, `switch`)
* Loops (`for`, `while`, `do-while`)
* Operators (`+`, `-`, `*`, `/`, `%`)
* Random number generation (`rand()`)

## 🎯 Activities for Day 7
Here’s a structured set of activities to help you learn holistically:

1️⃣ Improve Your Basic Calculator  
✅ Modify your existing calculator to:

* Handle invalid input (e.g., entering a letter instead of a number).
* Support floating-point calculations (use `double` instead of `int`).
* Allow repeated calculations until the user chooses to exit.

### 📌 Bonus: Add a power (^) and modulo (%) operator.

2️⃣ Build a Number Guessing Game
✅ Create a game where:  
1. The program **randomly selects** a number between **1 and 100**.  
2. The user **guesses the number**.  
3. The program tells them **"too high" or "too low"**.  
4. The game **continues until the correct number is guessed**.
5. After winning, the program **shows the number of attempts**.

📌 Bonus Challenges:
* Limit the number of guesses (e.g., **10 attempts max**).
* Add **difficulty levels** (easy: 1–50, hard: 1–500).
* Ask if the user **wants to play again**.

3️⃣ Debugging Practice
✅ Find and fix errors in these buggy code snippets:
I can provide broken code that you need to debug—let me know if you want some! 🛠️

4️⃣ Experiment with rand()
✅ Play around with the rand() function:

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    srand(time(0));  // Seed the random number generator
    printf("Random number: %d\n", rand() % 100 + 1);
    return 0;
}
```
📌 Try generating numbers in different ranges (1–10, 1–500, etc.).
