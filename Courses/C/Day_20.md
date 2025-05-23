
* [Syllabus](./C-Syllabus.md)  
* [Table of contents](./index.md)  
* [Day 19](./Day_19.md)  
* [Day 21](./Day_21.md)  

# Day 20: Array-based exercises (sorting algorithms, searching)

## 🧭 1. Introduction
Sorting and searching are fundamental operations on arrays in C and essential in computer science. Efficient data retrieval, comparison, and organization rely on these techniques. Learning how to implement them manually sharpens your algorithmic thinking and deepens your understanding of memory, loops, and control flow.

## 📋 2. Summary
You’ll learn to:
* Understand how linear and binary search algorithms work
* Implement bubble sort and selection sort in C
* Compare sorting/searching algorithm behaviors and efficiencies
* Trace and debug sorting and searching operations

## ✍️ 3. Concise Explanations
* **Linear Search**: Scans the array from start to finish to find a match.
* **Binary Search**: Divides a sorted array in half repeatedly to find the target.
* **Bubble Sort**: Repeatedly swaps adjacent elements if they are in the wrong order.
* **Selection Sort**: Selects the smallest (or largest) element and places it in the correct position.
* **Efficiency**: Sorting and searching algorithms have different time complexities; binary search is faster but requires sorted data.

## 🔍 4. Detailed Explanations
### 🔎 Linear Search
**Analogy**: Looking for your keys by checking every table and shelf, one by one.

```c
int linear_search(int arr[], int size, int key) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == key) {
            return i;  // Found at index i
        }
    }
    return -1; // Not found
}
```

### 🔎 Binary Search
**Analogy**: Searching a word in a dictionary — you flip to the middle, check, then go left or right.

```c
int binary_search(int arr[], int size, int key) {
    int left = 0, right = size - 1;
    while (left <= right) {
        int mid = (left + right) / 2;
        if (arr[mid] == key)
            return mid;
        else if (arr[mid] < key)
            left = mid + 1;
        else
            right = mid - 1;
    }
    return -1;
}
```
📌 Important: Only works if the array is already sorted.

### 🔁 Bubble Sort
**Analogy**: Like bubbles rising — larger elements "bubble" to the end.

```c
void bubble_sort(int arr[], int size) {
    for (int i = 0; i < size - 1; i++) {
        for (int j = 0; j < size - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}
```
🧠 Time Complexity: O(n²)

### 🔄 Selection Sort
**Analogy**: Sorting playing cards — select the smallest and place it first.

```c
void selection_sort(int arr[], int size) {
    for (int i = 0; i < size - 1; i++) {
        int min_idx = i;
        for (int j = i + 1; j < size; j++) {
            if (arr[j] < arr[min_idx])
                min_idx = j;
        }
        // Swap
        int temp = arr[i];
        arr[i] = arr[min_idx];
        arr[min_idx] = temp;
    }
}
````

#### 🔧 Diagram for Selection Sort (step-by-step)
```text
Unsorted:     [64, 25, 12, 22, 11]
Step 1:       [11, 25, 12, 22, 64]
Step 2:       [11, 12, 25, 22, 64]
Step 3:       [11, 12, 22, 25, 64]
Step 4:       [11, 12, 22, 25, 64] (done)
````

## 🧠 5. Exercises
### 🟢 Easy
1. Linear Search
Write a program that asks the user for an array of integers and a key, and prints the index of the key using linear search.

2. Print Sorted Array
Use bubble sort to sort a fixed array of integers and print the sorted result.

### 🟡 Medium
3. Binary Search on a Sorted Array
Prompt the user to enter 10 integers. Sort them using selection sort, then allow the user to search for a number using binary search.

4. Sort in Descending Order
Modify bubble sort so it sorts an array from largest to smallest.

### 🔴 Hard
5. Compare Sorting Performance
Write a program that fills an array with 1000 random numbers. Implement both bubble sort and selection sort. Measure and compare the time taken by each (use clock() from <time.h>).

6. Hybrid Sort Challenge
Combine selection sort and bubble sort: first use selection sort for the first half of the array, then bubble sort for the second. Print the sorted full array.

## 🔚 6. Recap and Next Steps
### ✅ What You’ve Learned
* Key search algorithms: linear and binary
* Key sorting algorithms: bubble and selection
* Efficiency matters: algorithm choice impacts performance
* Practical C skills: using loops, conditions, and array indexing

### 📘 Coming Up Next:
* Day 21: Dynamic Memory and `malloc`/`free`
You’ll learn how to allocate memory at runtime, build flexible data structures, and understand memory management in C.
