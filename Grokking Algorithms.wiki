--------------------------------------------------------------------------------
= Grokking Algorithms =
--------------------------------------------------------------------------------
== Important Terms ==
  Logarithms                 | Logarithms are the inverse of exponents.
                             | Example
                             |   Exponetial example: 10 ** 2 = 10 * 10 = 100
                             |     Ten to the power of 2 equals ten multiplied by ten equas 100
                             |
                             |   Logarithmic example: log10 100 == how many tens do we multiply to get 100?
                             |     Log10 100 = 10 ** X = 100
                             |
                             | Comparison:
                             |   10 ** 2 == log10 100  == 2
                             |   10 ** 3 == log10 1000 == 3
                             |    2 ** 3 == log2 8     == 3
                             |    2 ** 4 == log2 16    == 4
                             |    2 ** 5 == log2 32    == 5
                             |
  Linear Time                | An algorithm whose running time increases when
                             | the amount of items it must work with increases
                             |
--------------------------------------------------------------------------------
== Some common Big O run times (fastest to slowest) ==
  Log time                   | O(log n)     -- Example: Binary Search
  Linear time                | O(n)         -- Example: Simple Search
  O(n * log n)               | O(n * log n) -- Example: Quicksort
  O n squared                | O(n**2)      -- Example: Selection Sort
  O n Factorial              | O(n!)        -- Example: The Traveling Salesperson
                             |
                             |
                             |
                             |
                             |
                             |
--------------------------------------------------------------------------------
== Chap 1 takeaways ==
  * Algorithm speed isn't measured in seconds, but in growth of te number of operations.
  * Instead, wea talk about how quickly the run time of an algorithm increases
    as the size of the input increases.
  * Run time of algoritms is expressed in Big O notation.
  * O(log n) is faster than O(n), but it gets a lot faster as the list of items
    you're searching for grows.
                             |
--------------------------------------------------------------------------------

