[table of contents](./index.md)

# The C programming Language - Syllabus
## Week 1: Basics of C
* [Miscellaneous Notes](./misc_notes)
* [Day 1: Introduction to C, setting up the development environment (GCC, Clang, or an IDE like VS Code)](./Day_01.md)
* [Day 2: Writing and compiling a basic C program (printf, main, return 0;)](./Day_02.md)
* [Day 3: Data types, variables, and constants (int, float, char, const, #define)](./Day_03.md)
* [Day 4: Operators and expressions `(+, -, *, /, %, ++, --)`](Day_04.md)
* [Day 5: Control flow (if, else, switch)](Day_05.md)
* [Day 6: Loops (for, while, do-while)](Day_06.md)
* [Day 7: Simple exercises (basic calculator, number guessing game)](Day_07.md)

## Week 2: Functions and Pointers
* [Day 8: Function declaration, definition, and calling functions](Day_08.md)
* [Day 9: Function parameters and return values](Day_09.md)
* [Day 10: Recursion](Day_10)
* [Day 11: Introduction to pointers `(*, &, NULL)`](Day_11)
* [Day 12: Pointer arithmetic](Day_12)
* [Day 13: Function pointers](Day_13)
* [Day 14: Exercises (factorial using recursion, swapping two variables with pointers)](Day_14)

## Week 3: Arrays and Strings
* [Day 15: One-dimensional arrays](Day_15)
* [Day 16: Multi-dimensional arrays](Day_16)
* [Day 17: Strings (char arrays, gets, puts, strcpy, strlen)](Day_17)
* [Day 18: String manipulation functions (strcat, strcmp, strncpy)](Day_18)
* [Day 19: Pointers and arrays (relationship between pointers and arrays)](Day_19)
* [Day 20: Array-based exercises (sorting algorithms, searching)](Day_20)
* [Day 21: Mini-project: Simple text-based menu program](Day_21)

## Week 4: Memory Management and Structures
* [Day 22: Dynamic memory allocation (malloc, calloc, realloc, free)](Day_22)
* Day 23: Memory leaks and debugging tools (Valgrind)
* Day 24: Introduction to struct and typedef
* Day 25: Structs with pointers
* Day 26: Unions and bit fields
* Day 27: Linked lists introduction
* Day 28: Exercises (linked list operations)

## Week 5: File Handling and Advanced Topics
* Day 29: File I/O (fopen, fclose, fprintf, fscanf)
* Day 30: Reading and writing binary files
* Day 31: Command-line arguments (argc, argv)
* Day 32: Error handling (perror, strerror)
* Day 33: Preprocessor directives (#include, #define, #ifdef)
* Day 34: Macro functions and inline functions
* Day 35: Exercises (file-based student management system)

## Week 6: Concurrency, Best Practices, and Final Project
* Day 36: Multithreading with pthread
* Day 37: Process management (fork, exec)
* Day 38: Signals and handling (signal.h)
* Day 39: Best coding practices (modular programming, debugging)
* Day 40: Review and additional practice
* Day 41-42: Final project (small application like a phonebook, mini shell, or a simple game)

## After Course Considerations
If you complete the six-week plan and grasp the concepts well, you will have a strong foundation in C. However, to be well-versed in C, you'll need to go beyond the basics and intermediate concepts. Here’s what you should focus on next:

**1. Deep Dive into Pointers and Memory Management**
* Pointer to pointers `(char **argv)`
* Function pointers in real-world scenarios (callback functions)
* Advanced pointer arithmetic
* Memory alignment and padding
* Stack vs. heap memory usage

**2. Data Structures and Algorithms in C**
* Advanced Linked Lists (circular linked lists, doubly linked lists)
* Stacks and Queues (array-based and linked list-based implementations)
* Hash Tables (collision handling with chaining and open addressing)
* Trees and Graphs (binary trees, AVL trees, depth-first/breadth-first search)
* Sorting Algorithms (Merge Sort, Quick Sort, Heap Sort)
* Algorithm Optimization (profiling and reducing time complexity)

**3. Advanced File Handling and System Programming**
* File locking (fcntl.h, lockf)
* Memory-mapped files (mmap)
* Low-level I/O (read, write, open, close)
* Inter-process communication (pipes, message queues, shared memory)
* Daemon processes

**4. Concurrency and Multithreading**
* Advanced pthread usage (mutexes, condition variables)
* Thread synchronization and race conditions
* Using semaphores for resource management
* Thread pools and task scheduling

**5. Network Programming**
* Sockets (socket.h, bind, listen, accept)
* TCP vs. UDP socket programming
* Multi-threaded and asynchronous servers
* HTTP client/server implementation in C
* Select-based and epoll-based I/O multiplexing

**6. Embedded Systems and Low-Level Programming**
* Writing C code for microcontrollers (Arduino, STM32)
* Direct hardware access (memory-mapped registers)
* Interrupt handling and real-time constraints
* Assembly language interfacing (inline assembly)
* Optimizing for low memory and CPU cycles

**7. Compiler Internals and C Standards**
* How a C compiler works (preprocessing, compiling, linking)
* Writing your own compiler (tiny subset of C)
* Understanding C standard libraries (glibc, musl)
* Differences between C90, C99, C11, and C17
* Writing portable and standard-compliant C code

**8. Debugging and Performance Optimization**
* Using gdb and lldb for in-depth debugging
* Profiling with gprof, perf, and valgrind
* Avoiding memory leaks and buffer overflows
* Writing unit tests in C (CUnit, Check)
* Code coverage and static analysis tools (clang-analyzer, cppcheck)

**9. Security and Defensive Programming**
* Buffer overflow protection (Stack Canaries, ASLR)
* Secure coding practices (strncpy, fgets, avoiding gets)
* Reverse engineering and binary exploitation basics
* Writing hardened C code for secure applications

**10. Large-Scale Software Development in C**
* Modular programming with multiple files
* Makefiles and build automation (Make, CMake, Meson)
* Dynamic and static libraries (.a, .so, .dll)
* Version control and collaborative C development
* Writing C code for open-source projects

**Final Thoughts**
Mastering C requires not just learning these concepts but also practical application. Consider contributing to open-source C projects, solving problems on platforms like LeetCode, Codeforces, and Project Euler, or building a real-world application (e.g., a custom shell, a simple OS kernel, or a database engine).

Would you like help prioritizing which of these areas to focus on first based on your long-term goals?
