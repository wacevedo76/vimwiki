# Summaries

# The Python Apprentice
## Chapter 1 Summary - Getting Started:
  - Starting out with Python
    - Obtaining and installing Python 3
    - Starting the Read-Eval-Print-Loop or REPL
    - Simple arithmetic
    - Creating variables by binding objects to names
    - Printing with the built-in `print()` function  
<br>
  - Being Pythonic
    - Significant indentation
    - PEP 8 - They Style Guide for Python Code
    - PEP 20 - The Zen of Python
    - Importing modules with the import statement in various forms
    - Finding and browsing `help()`  
<br>
  - Basic types and control flow
    - `ints`, `floats`, `None`, and `bool`, plus conversions between them
    - Relational operators for equality and ordering tests
    - if-statements with `else` and `elif` blocks
    - while-loops with implicit conversion to bool
    - Interrupting infinit loops with `Ctrl-C`
    - Breaking out of loops with `break`
  - Requesting text from the user with `input()`
  - Augmented assignment operators  
<br>
## Chapter 2 Summary - Strings and Collections
  - `str` Unicode strings and `bytes` strings:
    - We looked at the various forms of quotes (single or double quotation 
        marks) for quoting srings, useful for incorporating quote marks
        themselves into strings. Python is flexible over which quoting style you
        use, but you must be consistent when delimiting a particular string
    - We demostrated that so-called triple quotes, consisting of three 
      consecutive quotation mark characters can be used to delimit a multi-line 
      string. Traditionally, each quote character is itself a double-quotation 
      mark, although single quotation marks can also be used.
    - We saw how adjacent string literals are implicitly 
      concatenated
    - Python has support for universal newlines, so no matter what platform you'
      re using it's sufficient to use a single `\n` character, safe in the 
      knowledge that it will be appropriately translated from and to the native 
      newline during I/O
    - Escape sequences provide an alternative means of incorporation newlines 
      and other control characters into leteral strings.
    - The blackslashes used for escaping can be a hindrance for Windows 
      filesystm paths or regular expressions, so raw strings with an `r` prefix 
      can be used to suppress the escaping mechanism
    - Other types, such as integers, can be converted to strings using the `str()` 
      constructor
    - Individual characters, returned, as one character strings, can e retrieved 
      using square brackets with integer zero-based indices.
    - Strings support a rich variety of operations, such as splitting, through 
      their methods
    - In Python 3, literal strings can contain any Unicode character directly in 
      the source, which is interpreted as UTF-8 by default
    - The `bytes` type has many of the capabilities of strings, but it is a 
      sequence as bytes rather than a sequence of Unicode code points.
    - `bytes` literals are prefixed with a lowercase `b`
    - To convert between string and bytes instances we use the `encode()` method 
      of `str` or the `decode()` method of `bytes`, in both cases passing the 
      name of the codec, which we must know in advance  
<br>
  - `list`
    - Lists are mutable, heterogeneous sequences of objects
    - List literals are delimited by square brackets and the items are separated 
      by commas
    - Individual elements can be retrieved by indexing into a list with square 
      brackets containing a zero-based integer index
    - In contrast to strings, individual list elements can be replaced by 
      assigning to the indexed item
    - Lists can be grown by `append()`-ing to them, and can be constructed from 
      other sequences using the `list()` constructor  
<br>
  - `dict`
    - Dictionaries associate keys with values
    - Literal dictionaries are delimited by curly braces. The key-value pairs 
      are separated from each other by commas, and each key is associated with 
      its corresponding value with a colon  
<br>
  - `for` loops
    - For-loops take items one-by-one from an iterable object such as a `list`, 
      and bind the same name to the current item
    - They correspond to what are called for-each loops in other languages  
<br>
## Chapter 3 Summary - Modularity
- Python Modules:
  - Python code is placed in `*.py` files called modules.
  - Modules can be executed directly by passing them as the first argument to the Python interpreter.
<br>
- Python functions:
  - Named functions are defined used the `def` keyword followed by the function name and he argument list parentheses.
  - We can return objects from functions using the `return` statement.
  - Return statements without a parameter return `None`, as does the implicit `return` at the end of every function body.
<br>
- Module execution:
  - We can detect whether a module has been imported or executed by examining the value of the special `__name__` variable. If it is equal to the string `"__main__"` our module has been executed directly as a program. By executing a function if this condition is met using the top-level `if __name__ == '__main__'` idiom at the end of our module, we can make our module both usefully importable and executable, and important testing technique even for short scripts.
  - The `def` keyword is a statement which binds executable code to a function name.
  - Command line arguments can be accessed as a list of strings accessible through the `argv` attribute of the `sys` module. The zero-th command line argument is the script filename, so the item at index one is the first true argument.
  - Python's dynamic typing means our functions can be very generic with respect to the type of their arguments.
<br>
- Docstrings:
  - A literal string as the first line of a function's definition forms the function's docstring. They are typically triple-quoted multiline strings containing usage information.
  - Function documentation provided in docstrings can be retrieved using `help()` in the REPL.
  - Module docstrings should be placed near the beginning of the module prior to any Python statements such as import statements.
<br>
- Comments:
  - Comments in Python commence with a hash character and continue to the end of the line.
  - The first line of the module can contain a special comment called a shebang, allowing the program loader to launch the correct Python interpreter on all major platforms.
<br>
## Chapter 4 Summary - Built-in types and the object model
- Python object reference
  - Think of Python working in terms of named references to objects rather than variables and values.
  - Assignment doesn't put a value in a box. It attaches a name tag to an object.
  - Assigning from one reference to another puts two name tags on the same objects with no name tag.
<br>
- Object identity and equivalence
  - The `id()` function returns a unique and constant identifier by should rarely, if ever, be used in production.
  - We can test for equivalence using the double-equals operator.
<br>
- Function arguments and return values
  - Function arguments are passed by object-reference, so functions can modify their arguments if they are mutable objects.
  - If a formal function argument is rebound through assignment, the reference to the passed-in object is lost. To change a mutable argument you should replace its *contents* rather than replacing the whole object.
  - the return statement also passes by object-reference. No copies are made.
  - Function arguments can be specified with defaults.
  - Default argument expressions are evaluated only once when the `def` statement is executed.
<br>
- The Python type system
  - Python uses dynamic typing, so we don't need to specify reference types in advance.
  - Python uses strong typing. Types are not coerced to match.
<br>
- Scopes
  - Python reference names are looked up in one of four nested scopes according to the LEGB rule: Local to functions, in Enclosing functions, in the Global (or module) namespace and Built-ins.
  - Global references can be read from a local scope.
  - Assigning to global references from a local scope requires that the reference be declared global using the global keyword.
<br>
- Objects and introspection
  - Everything in Python is an object, including modules and functions. They can be treated just like other objects.
  - The `import` and `def` keywords result in binding to named references.
  - The built-in `type()` function can be used to determine the tpe of an object.
  - The built-in `dir()` function can be used to introspect an object and return a list of its attribute names.
  - The name of a function or module object can be accesed through its `__name__` attribute.
  - The docstring for a function or module object can be accessed through its `__doc__` attribute.
<br>
- Miscellaneous
  - We can use `len()` to measure the length of a string.
  - If we "multiply" a string by an integer we get a new string with multiple copies of the operand string. This is called the "repetition" operation.
<br>
## Chapter 5 Summary - Exploring built in collection types
- Tuples are immutable sequence types
  - Literal syntax is optional parentheses around a comma-separated list.
  - Notable syntax for single lement tuples utilizing the trailing comma.
  - Tuple unpacking - useful for multipe return values and swapping.
<br>
- Strings
  - String concatenation is most efficiently performed with the `join()` method rather than the addition or augmented assignment operators.
  - The `partition()` method is a useful and elegant string parsing tool.
  - The `format()` method provided a powerful means of replacng placeholders with stringified values.
<br>
- Ranges
  - `range` objects represent arithmetic progressions.
  - The `enumerate()` built-in function is often a superior alternative to `range()` for generating loop counters.
<br>
- Lists
  - List support indexing from the end of the list with negative indices.
  - Slice syntax allows us to copy all, or part, of a list.
  - The full slice is a common Python idiom for copying lists, although the `copy()` method and `list()` constructor are less obscure.
  - List (and other colletions) copies in Python are shallow copies. References are copied, but the refered objects are not.
<br>
- Dictionaries map from keys to values
  - Iteration and membership testing with dictionaries is done with the respect to the keys.
  - The `keys()`, `values()`, and `items()` methods provide views onto the different aspects of a dictionary, allowing convenient iteration.
<br>
- Sets store and unordered collection of unique elements
  - Sets support powerful set-algebra operations and predicates.
  - The built in collections are organized according to which protocols they support, such as *iterable*, *sequence*, and *mapping*.
<br>
- In passing we have also discovered that
  - Underscore is commonly used for dummy or superfluous variables.
  - The `pprint` module supports pretty printing of compound data structures.
<br>
## Chapter 6 Summary - Exceptions
  - The rasing of an exception interrupts normal program flow and transfers control to an exception handler.
  - Exception handlers are defined using the `try --except` construct.
  - `try` blocks define a context in which exceptions an be detected.
  - Corresponding `except` blocks define handlers for specific types of exceptions.
  - Python uses exceptions pervasively and many built-in language features depend on them.
  - `except` blocks can capture an exception object, which is ofen of a standard type such as `ValueError`, `KeyError`, or `IndexError`.
  - Programmer errors such as `IndentationError` or `SyntaxError` should not normally be handled.
  - Exceptional conditions cn be signaled using the `raise` keyword which accepts a single parameter of an exception object.
  - `raise` without an argument within an `except` block re-raises the exception which is currently being processed.
  - We tend not to routnely check for `TypeErrors`. To do so would negate the flexibility afforded to us by Python's dynamic type system.
  - Exception objects can be converted to strings using the `str()` constructor for the purpose of printing message payloads.
  - The exceptions thrown by a function form a part of its API and should be appropriately documented.
  - When rasing exceptions prefer to use the most appropriate buit-in exception type.
  - Clean-up and restorative actions can be performed using the `try --finally` construct which may optionally be used in conjunction with `except` blocks.
<br>
- Along theway we saw
  - The output of the `print()` function can be redirected to `stderr` using the optinal `file` argument.
  - Python supports the logical operators and `and` and `or` for combining boolean expressions.
  - Return codes are too easily ignored.
  - Platform specific actions can be implemented using an Easier to Ask Forgiveness than Permission approach facilitated by intercepting `Import Errors` and providing alternative implementations.
<br>
## Chapter 7 Summary - Comprehensions, iterables, and generators
- Comprehensions are a concise syntax for describing lists, sets and dictionaries.
- Comprehensions operate on an iterable source object and apply an optional predicte item.
- Iterables objects are objects over which we can iterate item-by-item.
- We retrieve an iterator from an iterable object using the built-in `iter()` function.
- Iterators produce items one-by-one from the nderlying iterable series each time they are passed to the built-in `next()` function.
- Iterators raise a `StopIteration` exception when the collection is exhausted.
<br>
- Generators
  - Generator functions allow us to describe sequences using imperative code.
  - Generator functions contain at least one use of the `yield` keyword.
  - Generators are iterators. When the iterator is advanced with `next()` the generator starts or resumes execution up to and including the next `yield`
  - Each call to a generator function creates a new generator object.
  - Generators can maintain explicit state in local variables between iterations.
  - Generators are lazy and so can model infinite series of data.
  - Generator expressions have a similar syntactic form to list comprehensions and allow for a more declarative andconcise way of creating generator objects.
<br>
- Iterations tools
  -Python includes a set of tools for dealing with iterable series, both in the form of built-in functions such as `sum()`, `any()`, and `zip()` as well as in the `ittertols` module.
<br>
## Chapter 7 Summary - Comprehensions, iterables, and generators
  - Comprehensions are a concise syntax for describing lists, sets and dictionaries.
  - Comprehensions operate on a iterable source object and apply an optional predicate filter 
  - Iterables object are objects over which we can iterate item-by-item
  - We retrieve an iterator from an iterable object usng the built-in `iter()` function
  - Iterators produce items one-by-one from the underlying iterable series each time they are passed to the built-in `next()` function.
  - Iterators rais a `StopIteration` exception when the collection is exhausted.
<br>
- **Generators**
  - Generator functions allow us to desribe sequences using imperative code.
  - Generator functions contain at least one use of the `yield` keyword.
  - Generators are iterators. Whne the iterator is advanced with `next()` the generator starts or resumes execution up to and including the next `yield`.
  - Each call to a generator function creates a new generator object.
  - Generators an maintain explicit state in local variables between iterations.
  - Generators are lazy and so can model infinit series of data.
  - Generator expressions have a similar syntactic form to list comprehensions and allow for a more declarative and conciseway of creating generator.
<br>
- **Iteration Tools**
  - Python includes a rich set of tols for dealing with iterable series, both in the for of built-in functions such as `sum()`, `any()`, and `zip()` as well as in the `itertools` module
<br>
## Chapter 8 Summary - Defining new types with classes
  - All types in Python have a 'class'.
  - Classes define the structure and behavior of an object.
  - The class of an object is determined when the object is created and is almost always fixed for the lifetime of the object.
  - Classes are the key suppot for Object-Oriented Programming in Python.
  - Classes are defined using the `class` keyword followed by the class name, which is in CamleCase.
  - Instances of a class are created by calling the class as if it were a function.
  - Instance methods are functions defined inside the clas which should accept an object instance called `self` as the first parameter.
  - Methods are called using the `instance.method()` syntax which is syntactic sugar for passing the instance as the formal self argument to the method.
  - An option special initializer method called `__init__()` can be provided which is used to configure the `self` object at creation time.
  - The constructor calls the `__init__()` method if one is present.
  - The `__init__()` method is *not* the constructor. The object has been already constructd by the time the initializer is called. The initializer configures the newly created object before it's returned to the caller of the constructor.
  - Arguments passed to the constructor are forwarded to the initializer.
  - Instance attributes are brought into existence by assigning to them.
  - Attributes and methods which are implementation details are by convention prefixed with an underscore. There are no public, protected or private access modifiers in Python.
  - Access to implementation detals from outside the class can be very useful during development, testing anddebugging.
  - Class invariants should be established in the initializer. If the invariants can't be established raise exceptions to signal failure.
  - Methods can have docstrings, just like regular functions.
  - Classes can have docstrings.
  - Even within an object method calls must be qualified with `self`.
  - You can have as many classes and functions in a module as you wish. Related classes and global functions are usually grouped together this way.
  - Polymorphism in Python does not require shared base classes or named interfaces.
  - Polymorphism in Python is achieved through duck typing where attributes and methods are only resolved at point of use - a behavior called late-bindin.
  - Polymorphism in Python does not require shared base classes or named interfaces.
  - Class inheritance in Python does not require shared base classes or named interfaces.
  - All methods are inherited, including special methods like the initialiser.
  <br>
- Along the way we found that:
  - Strings support slicing, because they implement the *sequence* protocol.
  - Following the Law of Demeter can reduce coupling.
  - We can nest comprehensions.
  - It can sometimes be useful to discard the current item in a comprehension using a dummy reference, conventionally the underscore.
  - When dealing with one-based collections it's often easier just to waste the zeroth list entry.
  - Don't feel compelled to use classes when a simple function will suffice. Functions are also objects.
  - Complex comprehensions or generator expressions an be split over multiple lines to aid readability.
  <br>
## Chapter 9 Summary - Files and resource management
  - Files are opened using the built-in `open()`function which accepts a file mode to control read/write/append behaviour and whether the file is to be treated as raw binary or encoded text data.
  - For text data you should specify a text encoding.
  - Text files deal with string objects and perform universal newline translation and string encoding.
  - Binary files deal with `bytes` objects with no newline translation or encoding.
  - When writing files, it's your responsibility to provide newline characters for line breaks.
  - Files should always be closed after use.
  - Files provide various line-oriented methods for reading, and are also iterators which yield line by line.
  - Files are context managers and the with-statement can be used with context managers to ensure that clean up operations, such as closing files, are performed.
  - The notion of file-like objects is loosely defined, but very useful in practice. Exercise EAFP to make the most of them.
  - Context managers aren't restricted to file-like objects. We can use tools in the `contextlib` standard library module, such as the `closing()` wrapper to create our own context managers.
<br>
- Along the way we found that:
  - `Help()` can be used on instsance objects, not just types.
  - Python supports bitwise operators &, |, << and >>.
<br>
## Chapter 10 Summary - Unit testing with the Python standard library
  - The `unittest` module is a framwork for developing reliable automated tests.
  - you define *test cases* by subclassing from `unittest.TestCase`
  - The `setUp()` and `tearDown()` fixtures are used to run ocde before and after each test method.
  - Test methods are defined by creating method names that start with `test_` on test case objects
  - Use `TestCase.assertRaises()` in a with-statement to check that the right exceptions are thrown in a test.
<br>
## Chapter 11 Summary - Debugging with PDB
  - Python's standard debugger is called PDB.
  - PDB is a standard command-line debugger.
  - The `pdb.set_trace()` method can be used to stop program execution and enter the debugger.
  - Your REPL's prompt will change to (Pdb) when you're in the debugger.
  - You can access PDB's built-in help system by typing "help".
  - you can use `python -m pdb` followed by a script name to run a program under PDB from the start.
  - PDB's `where` command shows the current call stack.
  - PDB's `next` command lets execution continue to the next line of code.
  - PDB's `continue` command lets execution continue idefinitely, or until you stop it with control-c
  - PDB's `list` command shows you the source code at your current location.
  - PDB's `return` command resumes execution until the end of the current function.
  - PDB's `print` command lets you see the values of object in the debugger.
  - Use `quit` to exit PDB
<br>
- Along the way we found that:
  - `divmod()` calculates the quotient and remainder for a division operation at one time.
  - The `reversed()` function can revers a sequence.
  - You can pass `-m` to your Python command to have it run a module as a script.
- Dbuging makes it clear that Python is evaluating everthing at run time.
<br>

# The Python Journeyman
## Chapter 1 Summary - Organizing Larger Programs:
Packages are an important concept in Python, and in this chapter we've covered most of the major topics realated to implementing and working with them. Let's review the topcs we looked at:
  - **Packages**:
    - Packages are a special type of module
    - Unlike normal modules, packages can contain other modules, including other 
      packages
    - Packages hierarchies are a powerful way to organize related code
    - Packags have a `__path__` member which is a sequence specifying the 
      diretories from which a package is loaded
    - A simple standard project structure include a location from non-python 
      files, the project's package, and a dedicated test subpackage.  
<br>
  - **`sys.path`**:
    - `sys.path` is a list of directorires where Python serches for modules
    - `sys.path` is a normal list and can be modified and queried like any other 
      list
    - If you start Pyton with no arguments, an empty string is put at the front 
      of `sys.path`. This istructs Python to import modules from the current 
      directory
    - Appending directories to `sys.path` at runtime allows modules to be 
      imported from those directories  
<br>
  - **PYTHONPATH**:
    - **PYTHONPATH** is an evnironment variable containing a list of directories 
    - The format of **PYTHONPATH** is the same as for **PATH** on your system. 
      It's a semi-colon-separated list on Windows and a colon-separated list on 
      Linux or Mac OS
    - The contents of **PYTHONPATH** are added as entries to `sys.path`  
<br>
  - **`__init__.py`**:
    - Normal packages are implemented by putting a file names **`__init__.py`** 
      into a directory
    - The **`__init__.py`** file for a package is executed when the package is 
      imported.
    - **`__init__.py`** files can hoist attributes from submodule into higher 
      namespaces for convenience  
<br>
  - **Relative imports**:
    - Relative import allow you to import modules within a package without 
      specifying the full module path
    - Relative imports must use the `from module import name` form of import.
    - The "from" portion of relative import stars with at least one dot.
    - Each dot in a relative import represents a containing package
      the first dot in a relative import means "the package containing this module"
    -  Relative imports can be useful for reducing typing
    - Relative import can improve modifiability in some cases
    - In general, it's best to avoid relative imports because they can make code 
      harder to understand  
<br>
  - **Namespace packages**:
    - A namespace package is a package split across several directories
    - Namespace packages are described in **PEP420**
    - Namespace packages don't use `__init__.py` files
    - Namespace packages are created when one or more directories in the Python 
      path match an import request and no normal packages or modules match the 
      request.
    - Each directory that contributes to a namespace package is listed in the 
      package's `__path__` attribute.  
<br>
  - **Executable directories**:
    - Executable directories are created by putting a `__main__.py` file in a 
      directory
    - You execute a directory with Python by passing it to the Python executable 
      on the command line
    - When `__main__.py` is executed its `__name__` attribute is set to 
      `__main__`
    - When `__main__.py` is executed, its parent directory is automatically 
      added to `sys.path`
    - The `if __name__ == '__main__':` construct is redundant in a `__main__.py` 
      file
    - Executable directories can be compressed into zip-files which can be 
      executed as well
    - Executable directoires and zip-files are convenient wasy to distribute 
      Python programs  
<br>
  - **Modules**:
    - Modules can be executed by passing them to Python with the `-m` argument
    - The `_all__` atrtribute of a module is a list of strings specifying the 
      names to export when `from module import *` is used
    - Module-level attribues provide a good mechanism for implementing 
      singletons
    - Modules have well-defined initialization semantics  
<br>
  - **Miscellaneous**:
    - The standard `gizp` module allows you to work with files compressed using 
      GZIP
    - The standard `bz2` module allows you to work with files compressed using 
      BZ2
<br>
## Chapter 2 Summary - Beyond Basic Functions  
  Understanding callable objects and Python's calling syntax is a critical step in effective use of Python, and in this chapter we've covered the important details of each. The topics we've looked at include:
  - **Callable objects**: 
    - The idea of functions can be generalised to the notion of *callables*
    - We can make callable objects from instances by implementing the special `
      __call__()` method on our classes and then invoking the object as if it 
      were a function
    - Callable instances allow us to define "functions" which maintain state 
      between cals
    - Callable instances also allow us to give "functions" attributes and 
      methods which can be sued to query and modify that state
    - Whenever we create an object by invoking a constructor, we're actually *
      calling* a class object. Class objects are themselves callable
    - Class objects can be used just like any other callable object, including 
      being passed to, and returned from, functions, and bound to names through 
      assignment
    - Calable objects can be detected using the built-in `callable()` predicate 
      function  
<br>
  - **Lambda expressions**:
    - A single expression can be used as a callable by creating a `lambda` which 
      is an anonymous callable
    - `Lambdas` are most frequently used inline and passed directly as arguments 
      to other functions
    - Unlike regular functions, the `lambda` argument list isn't enclosed in 
      parentheses
    - The `lambda` body is restricted to being a single expression, the value of 
      which will be returned  
<br>
  - **Extended parameter and call syntax**:
    - Extended parameter syntax allows arbitrary positional arguments to be 
      accepted using the *star-args* syntax in the callable definition, which 
      results in arguments being packaged into a tuple
    - Similarly, arbitrary keyword arguments can be accepted using the *double-
      star-kwargs* syntax which results in the keyword arguments being packaged 
      into a dictionary
    - extended call syntax allows us to unpack iterable series and mappings into 
      positional and keyword function parameters 
      respectively
    - There is no requirement for use of `*` and `**` at the call-site to 
      correspond to the use of * and ** in the definition. Arguments will be 
      unpacked and repacked into the parameters as necessary
    - `*args` and `**kwargs` can be combined with mandatory positional and 
      keyword arguments in a well-defined order  
<br>
  - **Miscellaneous**:
    - The `timeit` module can be used to measure the performance of small code 
      snippets
    - Python supports a syntax for conditional expressions of the form 
      **`result = true_value if condition else fales_value`**
    - `zip()` uses extended argument syntax to accept an arbitrary number of 
      iterable series as arguments. By combining `zip()` with the extended call 
      syntax using `*` to unpack an iterable series of iterable series, we can 
      transpose two-dimensional tables of data, converting rows into columns and 
      vice-versa
    - the `list(zip(*table))` idiom is widespread enough that you need to be able to recognise it on sight
<br>
## Chapter 3 Summary - Closures and Decorators
- Local functions:
  - `def` is executed at runtime
  - `def` defines functions in the scope in which it is called, and this can e inside other functions
  - Functions defined inside other functions are commonly called *local functions*.
  - A new local function is created each time the containing function is executed
  - Local functions are no different from other local name bindings and can be treated like any other object
  - Local functions cna access names in other sopes vie the LEGB rule.
  - The enclosing scope for a local function includes the parameters of its enclosing function.
  - Local functions are similar to lambdas, but are more general and powerful
  - Functions can retune other functions, including local function defined in their body.
<br>
- Closures:
  - Closures allow local functions to access objects from scopes which have terminated.
  - Closures ensure that objects from terminates scopes are not garbage collected.
  - Functions with closures have a special `__closure__` attribute.
  - Local functions and closures are the keys to implementing *function factories* which are functions that create other functions.
<br>
- Function decorators:
  - Function decorators are used to modify the behavior of existng functions without having to change them directly.
  - Decorators are called objects which accept a single callable object as an argument and return a new callable object.
  - You use the `@` symbol to apply decorators to functions.
  - Decorators can enhance the maintainability, readability, and scalability of designs.
  - Decorators can be any kind of callable object. We looked specifically at functions, class objects, and class instances.
  - When class objects are used as decorators the resulting callable is a new instance of that class.
  - When class instances are used as decorators, the result of thei `__call__` method becomes the new callable.
  - Multiple decorators can be applied to a function.
  - When multiple decorators are used, they are applied in reverse order.
  - Decorators are composable: they don't have to be specially designed to wokr with other decorators.
  - Class-methods can be decorated just like functions.
  - Decorators are a powerful tool, but make sure that you don't overuse them or use them unnecessarily.
  - Technically, decorators never take any arguments except the callable that they decorate:
    - To parameterize decorators, you need a decorator factory that creates decorators.
  - Local functions can create closures over objects in any number of enclosing scopes.
  - The `__name__` and `__doc__` attributes of decorated functions are actually those of their replacement function, which is not always what you want.
  - You can manually update the `__name__` and `__doc__` attributes of your wrapper functions.
  - The `functools.wraps()` function can be used to create well-behaved wrappers in a simple and clear manner.
<br>
## Chapter 4 Summary - Properties and Class Methods
- Class and instance attributes
  - Covered the distinction between class attributes and instance attribures
  - Demonstrated how class attributes are shared between all instance of a class
  - Shown how to refer to class attributes from within or without the class definition by fully qualifying them with the class name.
  - Warned against attempting to assign to class attributes through the `self` instance, which actually creates a new instance attribute.
<br>
- static- and class-methods
  - Used the `@staticmethod` decorator to define methods within the class which do not depened on either class or instane objects
  - Used the `@classmethod` decorator to define methods which operate on the class object.
  - Implemented an idiom called *named constructors* using class methods.
  - Shown how static and class method behave with respect to inheritance.
  - Shown that static and clas methods can support polymorphic method dispatch when invoked through an instance rather through a class.
<br>
- Properties
  - Introduced properties to wrap attributes with getters and optional setter methods using the `@property` decorator.
  - Finally, we showed an easy way to override properties by applying the *template method* design pattern.
<br>
## Chapter 5 Summary - Strings and Representations
- `str()` and `repr()`
  - Python has two primary string representations for objects, `str()` and `repr()`.
  - The `str()` function is used to create `str` representations, and it relies on the `__str__` method.
  - The `repr()` function is used to create `repr` representations, and it relies on the `__repr__()` method.
  - `__repr__()` should produce an unambiguous, precise representation of the object.
  - `__repr__()` should include the type of and any identifying information for the object.
  - The `repr()` form is useful for context like debuggin and logging where information is more important than human readability.
  - You should always implement `__repr__()` on your classes.
  - The default `__repr__()` implementation is not very useful.
  - The `str()` form is intended for human consumption, and doesn't need to e as precise as `repr()`
  - The `print()` function uses the `str` representation.
  - By default, `__str__()` uses `__repr__()`.
  - The default `__repr__()` does **not** use `__str__()`
  - Built-in collections like `list` use `repr()` to print their elements, even if te collection itself is printed with `str()`.
  - Good `__repr__()` implementations are easy to write and can improve debugging.
  - When reporting errors, the `repr()` of an object is generally more helpful than the `str()`.
<br>
- `format()`
  - `str.format()` uses an object's `__format__()` method when inserting it into string templates.
  - The dafault implementation of `__format__()` is to call `__str__()`.
  - The argument to the `__format__()` method contains any special formatitng instructions from the format string
    - These instructions must come after a colon between the curly braces for the object
  - In general you do not need to implement `_format__()`
<br>
- `reprlib`
  - `reprlib` provides a drop-in replacement for `repr()` which limit output size 
  - `reprlib` is useful when printing large data structures.
  - `reprlib` provides the class `Repr` which implements most of `reprlib`'s functionality.
  - `reprlib` instantiates a singleton *Repr* called *aRepr*
  - `reprlib.repr()` is the drop-in replacement for `repr()`
    - This function is just an alias for `reprlib.aRepr.repr()`
  - The *Repr* clas is designed to be extended and customized via inheritance
<br>
- More string functions:
  - The function `ascii()` replaces non-ASCII characters in a Unicode string with escape sequences.
  - `ascii()` takes in a Unicode string and returns a Unicode string.
  - The `ord()` function takes a singlecharacter Unicode string and returns the integer codepoint of that character.
  - The `chr()` function takes an integer codepoint and returns a single-character string containing that character.
  - `ord()` and `chr()` are inverses of one another.
<br>
## Chapter 6 Summary - Numeric and Scalar Types
- Basic numeric types
  - Reviewed the capabilities of the *int* and *float* types and looked at how to query `sys.float_info` to get details of the *float* implementation.
  - Understood the limitations of finite precision of the *float* type and the impact this has on representing numbers in binary.
<br>
- `decimal.Decimal`
  - We introduced the *decimal* module which provides another floating point numeric type founded on base 10 and with user configurable precision.
  - We explained that `Decimal` is preferred for certain financial applications, such as accounting where the problem domain inherently decimal in nature.
  - We highlighted some key differences in behaviour between *Decimal and the other numeric types, particularly in the behaviour of integer division and modulus operator, which for *Decimal* truncates twards zero, but for *int* and *float* round towards negative infinity. This has implications for correctly writing functions which may need to work correctly with various number types.
<br>
- We demonstrated support for rational numbers using the *Fraction* type from the `fractions` module, showing how to construct and manipulate *Fraction( values using arithmetic.
<br>
- *complex*
  - We introduced the built-in *complex* type and gave an overview of complex number support in Python, including the `cmath` module which includes complex equivalents of the functions in the `math` module.
  - We gave a brief demonstration of the utility of complex numbers in Python by using them to solve a simple electrical engineering problem, determining the properties of AC current in a simple circuit.
<br>
- built-in features
  - `abs()` for computing the distance of a number from zero - which also works for complex numbers.
  - `round()` which rounds to a specified *decimal* precision, and the surprises this can lead to when used on *floats* which are internally represented in binary.
  - We reviewed the literal syntax for numbers in different bases.
  - And showed how to convert to strings in these literal forms using the built-in `bin()`, `oct()` and `hex()` functions.
  - We demonstrated how to convert from strings in bases 2 to 36 inclusive by using the *base* argument to the `int()` constructor, and how to convert from any numeric iteral in string form by specifying base zero.
<br>
- Date and time
  - We covered the representation of dates, times and compound date-time objects using the facilities of the `datetime` module.
  - We explained the difference between naive and timezone-aware times.
  - And the many named constructors available for construction time related objects.
  - We showed string formatting of time and date objects and how to parse these strings back into datetime objects.
  - We explained how durations can be modelled with the `timedelta` object and how to perform aarithmetic on *datetimes*.
  - We demonstrated the basic tie zone support available in Python 3 with the `timezone` class and referred you to the third-party `pytz` package for more comprehensive support.
- We showed how regular floats can be unsuitable for geometric computation owing to finite precision, and how to solve this by deploying the `Fraction` type in geometric computation.
<br>
## Chapter 7 Summary - Iterables and Iteration
- Comprehension
  - Comprehensions can process more than one input series
  - Multiple input series in comprehensions work like nested for-loops.
  - Comprehensions can also hae multiple if-clauses interspersed with the for-clauses
  - Later clauses in a comprehension can reference variables bound in earlier clauses.
  - Comprehensions can also appear in the result expressions of a coprehension, resulting in nested result series.
- Python provides a number of functiona-style tools for working with iterators
- `map`
  - `map()` calls a function for each element in its input series.
  - `map()` returns an iterable object, not a fully-evaluated collection
  - `map()` results are lazily evaluated, meaning that you must access them to force their calculation.
