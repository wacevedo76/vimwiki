--------------------------------------------------------------------------------
General programming Conecepts
--------------------------------------------------------------------------------
== Iterables ==
  When you create a list, you| >>> mylist = [1, 2, 3]
  can read its items one by  | >>> for i in mylist:
  one. Reading its items one |         print(i)
  by one is called iteration |
                             |
  so list, tuples, hashes    | mylist = [x*x for x in range(3)]
  dictionarys are iterables  | for i in mylist:
                             |     print(i)
  Iterables are handy becase |
  becaues they can be read   |
  and manipulated at any time|
                             |
  Unfortunatley, they are    |
  stored in memory, so it    |
  isn't always ideal for     |
  large sets of data         |

== Generators == 
  Generators are iterators, a| mygenerator = (x*x for x in range(3))
  kind of iterable you can   |
  5only iterate over once.   |
  Generators do not store all|
  the values in memory, they |
  generate the values on the |
  fly:                       |

== Yield ==
  yield is a keyword that is | To master yield, you must understand that when you
  used like return, except   | call the function, the code you have writtern in 
  the function will return a | the function body does not run. The function only
  generator.                 | returns the generator object.
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
