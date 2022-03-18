[[../Python|index]]
--------------------------------------------------------------------------------
  Modules                    |
    import statement         | import <module>
      must use full module   | import random
      name in function call  |
                             |
    import from statement    | from <module> import <function>
      can now use bare       | from random import *
      function call          |
                             |
Terminating a function call  | import sys
early                        | sys.exit()
                             |
importing modules from a dir | import sys
other than the script dir    | sys.path.append(directory of module)
                             |
Run module files             | exec(open('script.py').read())
                             |
