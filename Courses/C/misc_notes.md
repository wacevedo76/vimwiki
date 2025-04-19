* [table of contents](./index.md)
* [Syllabus](C-Syllabus)

# Miscellaneous Notes

## Functions quick Notes
### `scanf`
The `scanf` function is used to take input from the user.
* It requires **format specifiers** (like "%d" for integers).
* The `&` **(address-of) operator** is used for variable input (except for `char[]`).

## Chapter 9 Misc Notes
🧠 TL;DR - Common Gotchas Recap:

| Mistake                                           | Fix                                 | Why                                 |
| ---------------------------------------           | ---------------------------         | ------------------------------      |
| `scanf("%d", value);`                             | `scanf("%d", &value)`;              | You must pass the address           |
| Forgetting to trim newline from `fgets`           | Use `strcspn(prompt, "\n")`         | To avoid weird string behavior      |
| Passing dereferenced pointers to string functions | Use the pointer directly (`char *`) | `%s` expects a `char *`, not `char` |

### Question for ChatGPT
```
Okay, let me see if I understand how variable assignment works in C.
For example, the variable declaration: char example[10]' creates three entities:
1. A label (maybe it is called something else) that points the a memory address
2. The memory address, or in this can, a series of memory addresses. 
3. and each address points to a value.

is this a correct way of thinking?
```

#### 1. A label (or identifier) that points to a memory address
✅ Correct.  
In your example, `example` is the name of the array (an identifier) and also   
acts as a pointer to the first element of the array.  

So `example` (without brackets) gives you the address of the first element: `&example[0]`.  

#### 2. The memory address, or in this case, a series of memory addresses
✅ Correct.  
The array allocates 10 consecutive bytes of memory (because each char is 1 byte  
in C). So example[0], example[1], ..., example[9] are stored in adjacent memory  
locations.

#### 3. Each address points to a value
✅ Exactly.  
Each of the 10 addresses stores a char value (an integer between -128 to 127  
or 0 to 255 depending on whether char is signed or unsigned on your system).  
Initially, the contents may be garbage until you initialize or assign values.

#### 🔍 Bonus: How You Can Think About It in Terms of Memory
Suppose the array starts at memory address 0x1000. Then you might imagine:


| Index        | Address  | Value                          |
| -----        | -------  | -----                          |
| `example[0]` | `0x1000` | `'W'`                          |
| `example[1]` | `0x1001` | `'i'`                          |
| `example[2]` | `0x1002` | `'l'`                          |
| ...          | ...      | ...                            |
| `example[9]` | `0x1009` | `'\0'` (maybe null terminator) |

And:
* example → 0x1000 (type `char *`)
* *example → value at 0x1000, i.e., example[0]
* example + 1 → 0x1001, so *(example + 1) is example[1]

#### 🧠 Summary
Yes, your intuition is solid:

A variable like `char example[10]` gives you a label (`example`) that refers to a  
block of 10 addresses, each of which stores a value (`char`), and the name of the  
array can be treated like a pointer to its first element.

If you keep thinking like this, you'll **really shine** when you hit Day 11:  
Pointers. Would you like a little visual diagram to go along with this?



## 🔢 Three Ways of Passing Information to Functions
In C, when you define function parameters, you're essentially choosing **what 
you're** passing and **how you're passing it**:

### 1. Passing the value (a copy of the actual value)
This is called **pass by value**.

* Example:
```c
void printSquare(int num) {
    printf("%d\n", num * num);
}
```
* `num` is a copy of the value passed in.
* Changing `num` in the function does not affect the original variable.

#### ✅ You're passing the value.

### 2. Passing the address (a pointer to the original data)
This is called **pass by reference** (although technically, C only has pass by  
value—you're just passing a value that happens to be an address).

* Example:
```c
void update(int *ptr) {
    *ptr = 10;
}
```
* `ptr` is a **pointer**, which stores the address of the variable you want to modify.
* Using `*ptr` (dereferencing), you can access or modify the original value.

#### ✅ You're passing the address, and using it to access the original value.

### 3. Passing the identifier of a compound structure (like arrays or structs)
In C, when you pass arrays (like `char[]`), you're actually passing **a pointer to  
the first element**.

* Example:
```c
void greet(char name[]) {
    printf("Hello, %s!\n", name);
}
```
name decays into a pointer (char `*`) to the first character.
You can read or modify the array contents through this.

✅ You're passing a reference to a compound value, via its pointer.

⚠️ C does not support passing variables by reference like C++ (with &). It always passes a copy of the value—if that value is an address, you can use it to indirectly modify things.

#### 🧠 Summary Table

| What You Pass         | Function Parameter Example | Can Modify Caller’s Variable? | Notes                       |
| --------------------- | -------------------------- | ----------------------------- | --------------------------- |
| Value                 | void func(int x)           | ❌ No                         | Pass by value               |
| Address (Pointer)     | void func(int *x)          | ✅ Yes                        | Pass by pointer (reference) |
| Array (decays to ptr) | void func(char str[])      | ✅ Yes                        | Treated as char *str inside |

So your thinking is absolutely right—you can define parameters that are:
1. **The value**
2. **The address** (pointer)
3. **The identifier** (which becomes a pointer when arrays are involved)

### 🧪 Code: Passing Value, Address (Pointer), and Array (Identifier)
```c
#include <stdio.h>

// 1. Passing by value (copy)
void changeValue(int num) {
    num = 100;
    printf("Inside changeValue: num = %d\n", num);
}

// 2. Passing by address (pointer)
void changeValueByPointer(int *numPtr) {
    *numPtr = 200;
    printf("Inside changeValueByPointer: *numPtr = %d\n", *numPtr);
}

// 3. Passing an array (decays into pointer)
void modifyArray(char arr[]) {
    arr[0] = 'Z';  // Modify the first character
    printf("Inside modifyArray: arr = %s\n", arr);
}

int main() {
    // --- 1. Pass by Value ---
    int x = 10;
    printf("Before changeValue: x = %d\n", x);
    changeValue(x);
    printf("After changeValue: x = %d\n\n", x);

    // --- 2. Pass by Pointer ---
    int y = 20;
    printf("Before changeValueByPointer: y = %d\n", y);
    changeValueByPointer(&y);
    printf("After changeValueByPointer: y = %d\n\n", y);

    // --- 3. Pass Array (as pointer) ---
    char name[] = "Alice";
    printf("Before modifyArray: name = %s\n", name);
    modifyArray(name);
    printf("After modifyArray: name = %s\n", name);

    return 0;
}
```

#### 🧾 Sample Output:
```yaml
Before changeValue: x = 10
Inside changeValue: num = 100
After changeValue: x = 10

Before changeValueByPointer: y = 20
Inside changeValueByPointer: *numPtr = 200
After changeValueByPointer: y = 200

Before modifyArray: name = Alice
Inside modifyArray: arr = Zlice
After modifyArray: name = Zlice
```
#### 🧠 What This Shows:
* `changeValue(x)` doesn't affect `x` because it gets a copy of `x`.
* `changeValueByPointer(&y)` does change `y`, because it receives the **address**, and dereferences it.
* `modifyArray(name)` changes the array because arrays are passed as **pointers to the first element**, so the function works directly on the original data.

Let me know if you want a visual diagram of this or if you’d like to experiment by adding structs or strings into the mix next. 😊

