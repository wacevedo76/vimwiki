# Notes on Recursion
## Initial question to the LLM
> thank you for the clarification. On a different topic, I understand the general method of creating a
  recursive function; a function that calls itself for an undetermined but not infinite number of times
  in order to perform some task where the number of iterations is undetermined, but not infinite. I am
  having trouble structuring a basic recursive function though, specifically with the return value of
  the recursive function. If i set the value for the return value at the beginning of the function, won't
  that value reset to its initial assignment every time the function is called?
## Response
✦ That is an excellent question, and you've correctly identified one of the most common hurdles when
  learning recursion.

  You are exactly right. If you initialize a variable at the beginning of a recursive function, its
  value will be reset to that initial assignment every time the function calls itself.
```
    1 function wrongSum(numbers) {
    2   let total = 0; // This will be reset to 0 on every recursive call
    3
    4   if (numbers.length === 0) {
    5     return total;
    6   }
    7
    8   total += numbers[0];
    9   return wrongSum(numbers.slice(1)); // This will always return 0
   10 }
```

  There are two primary patterns to solve this and correctly manage the state (like a return value)
  through recursive calls.

### Pattern 1: Pass the State as an Argument

  Instead of initializing the state inside the function, you pass it as an argument to the next
  recursive call. This is often done with an "accumulator" variable.

  Each call receives the current state, adds its own contribution, and passes the new state to the
  next call.
```
    1 // The 'sum' parameter acts as our accumulator
    2 function sumArray(arr, sum = 0) {
    3   // 1. Base Case: When the work is done, return the final accumulated value.
    4   if (arr.length === 0) {
    5     return sum;
    6   }
    7
    8   // 2. Recursive Step: Do a small piece of work and call the function again
    9   //    with an updated state.
   10   const newSum = sum + arr[0];
   11   const restOfTheArray = arr.slice(1);
   12
   13   return sumArray(restOfTheArray, newSum);
   14 }
   15
   16 const numbers = [10, 5, 3];
   17 const total = sumArray(numbers); // 18
   18
   19 /*
   20 How it works:
   21 1. sumArray([10, 5, 3], 0)
   22 2.   -> calls sumArray([5, 3], 10)
   23 3.     -> calls sumArray([3], 15)
   24 4.       -> calls sumArray([], 18)
   25 5.         -> returns 18 (base case)
   26 */
```

  ### Pattern 2: Use a Wrapper Function (Closure)

  You can define an outer "wrapper" function that initializes your result variable one time. Inside
  it, you create a second, inner function that performs the recursion. This inner function has
  access to the outer function's variables (this is called a "closure") and can modify them.
```
    1 function collectOddNumbers(arr) {
    2   // 1. Initialize the result array just once in the outer function.
    3   const oddNumbers = [];
    4
    5   // 2. Create an inner recursive helper function.
    6   function find(inputArray) {
    7     // Base Case
    8     if (inputArray.length === 0) {
    9       return; // We're done, just stop.
   10     }
   11
   12     // Action
   13     if (inputArray[0] % 2 !== 0) {
   14       oddNumbers.push(inputArray[0]); // Modify the outer 'oddNumbers' array
   15     }
   16
   17     // Recursive Step
   18     find(inputArray.slice(1));
   19   }
   20
   21   // 3. Start the recursion.
   22   find(arr);
   23
   24   // 4. Return the final result.
   25   return oddNumbers;
   26 }
   27
   28 const numbers = [1, 2, 3, 4, 5, 6];
   29 const odds = collectOddNumbers(numbers); // [1, 3, 5]
```

  Pattern 1 is generally preferred in functional programming as it avoids side effects (modifying
  external variables), but Pattern 2 is also very common and can be easier to understand when you're
  starting out.
