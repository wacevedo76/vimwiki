[[../Python|index]]
--------------------------------------------------------------------------------
= Hashes / Dictionaries =
--------------------------------------------------------------------------------
== Hashes / Dictionaries in Python ==
  Keys, values, items        | {}.keys()
  These return types, while  | {}.values()
  not actually arrays, can   | {}.items
  be used in loops           |
                             |
                             | for k in spam.keys()
                             | for i in spam.items() --> ('key', 'value')
                             | for k, v in spam.itmes()
                             |
  Checking whether a key or  | 'name' in spam.keys()
  value exists in dictionary | 'william' in spam.values()
  returns boolean value      |
                             |
  Get()                      | picnicItems = {'apples': 5, 'cups': 2}
    Checks to see if a key   | picnicItems.get('cups'; 0)   --> returns the number of cups or 0
    exists, returns the      |
    value or an fallback     |
                             |
  Setdefault                 | spame.setdefault('color', 'black')
    Sets a default value for |
    key which is called but  |
    does not already exist   |
--------------------------------------------------------------------------------
