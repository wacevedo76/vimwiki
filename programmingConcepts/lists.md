[[../Python|index]]
--------------------------------------------------------------------------------
= Lists =
--------------------------------------------------------------------------------
== Lists in Python 3 ==
  list()                     | list('hello') -> ['h','e','l','l','o']
                             |
                             | list.index(<element>) <-- can take a start index
                             |                        as second argument
                             | list.count(value) <-- returns the number of times
                             |                    a value occurs in list
                             | list.append(<element>) <-- adds 1 item to lists end
                             | list.extend([<list>]) <-- adds multi items to end
                             | list.insert(index, item)
                             | list.clear() <--  removes ALL items from list
                             | list.pop() <-- default, removes the last elemnt
                             |                can add index as first argument
                             | list.remove(<element>)
                             | list.sort() | (reverse=True), (key=str.lower)
                             |
                             | list.reverse()
                             |
  Search for an item in list | '<value>' in <list>  --> returns boolean
                             | '<value>' not in <list>  --> returns boolean
                             |
  enumerate()                | Enumerate will iterate over an iterable and return
                             | two values on each iteration, the index of the
                             | item and the
                             |
                             | for index, item in enumerate(supplies)
                             |
  random                     | import random
                             | random.choice([])
                             | random.shuffle([])
                             |
  copy                       | import copy
    newList = list           |
    does not make a new list | newList = copy.copy(originalList)
    it only makes a reference| newList = copy.deepcopy(originalList)
    to the original list     |     (use deepcopy if origianl list has lists)
--------------------------------------------------------------------------------
