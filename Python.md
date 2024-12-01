--------------------------------------------------------------------------------
# Python notes
## Books 
[Automate the Boring Stuff](AtBS)  
[The Python Journeyman Series](Python/ThePythonJourneyman_notes)

## Misc
* [Defined Terms](programmingConcepts/Terms)  
* [Environment](Python/environment)
* [Built-ins](programmingConcepts/builtins)  
* [Common Modules](common_modules)  
* [Common useful commands](Python/common_useful_commands)  
* [Lists](programmingConcepts/lists)  
* [Strings](Concepts/Types/Python/strings)  
* [Hash/dictionary](programmingConcepts/hash-dict)  
* [Modules](programmingConcepts/Modules)  
* [oop](Concepts/oop/python_oop)
* [Error Handling](programmingConcepts/Error_handling)  
* [Bitwise Operators](Python/bitwise)
* [Testing](Python/Testing/unittest)  
* [Web Scraping](Python/web_scraping.wiki)  
* [pdb](Python/pdb)

## Tools
* [Ipython](Python/ipython)

## Python Data Model
You can think of the Python data model as a description of Python as a framework.  
It formalizes the interfaces of the building blocks of the language itself, such  
as sequences, functions, iterators, coroutines, classes, context managers, etc.  

As an example, when requesting `object[key]`, the interpreter calls  
`object.__getitem__(key)`  
Special methods are implemented when we want our objects to support and interact  
with fundamental language constructs such as:
* Collections
* Attribute access
* Iteration (including asynchronous iteration using **_async for_**)
* Operator overloading
* Function and method invocation
* String representation and formatting
* Asynchronous programming using **_await_**
* Object creation and destruction
* Managed context using the **_with_** or **_async with_** statements

**Note**:  
* **_magic method_** is a term used to refer to a _special method_. which are  
  also refered to as **_dunder method_** (double underscore methods)

## File and Resource Management

### Terms:
* **Context Manager**
  A Context Manager is a construct that provides a vonvenient way to manage 
  resources such as files, network connections, or locks. The context manager 
  ensures that resource is properly acquired and released, even in the face of
  exceptions.  

### Reading and Writing files  

| Objective                                          | File operator (fo) method                           |
| -------------------------------------------------: | :-----------------------------------------------    |
| Open a file (creating a file object (fo))          | `fo = open(<file path>, <mode>, <encoding>`         |
| Read all data from a file object                   | `fo.read()`                                         |
| Only read a specific number of characters          | `fo.read(<character position int>)`                 |
| Move the file pointer to the beginning of the file | `fo.seek(0)`                                        |
| Read one line at a time                            | `fo.readline()`                                     |
| Return a list of all the lines of a file           | `fo.readlines()`                                    |
| Write multiple lines                               | `fo.writelines(['list','of','lines'])`              |
| with-block                                         | `with open(filename, mode='rt', encoding='utf-8'):` |

#### Mode Codes  

| Code | Meaning                                                                                                                                                                                                                                                                                                                         |
| :--: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------                                                                      |
| r    | Open file for reading. The stream is positioned at the beginning of the file (default)                                                                                                                                                                                                                                          |
| r+   | Open for reading and writing. The stream is positioned at the beginning of the file                                                                                                                                                                                                                                             |
| w    | Truncate file to zero length or create file for writing                                                                                                                                                                                                                                                                         |
| w+   | Open for reading and writing. The file is created if it does not exist, otherwise it is truncated. The stream is positioned at the beginning of the file                                                                                                                                                                        |
| a    | Open for writing. The file is created if it does not exist. The stream is positioned at the end of the file. Subsequent writes to the file will always end up at the end of file, irrespective on any intervening seks or similar                                                                                               |
| a+   | Open for reading and writing. The file is created if it does not exist. The stream is positioned at theend of the file. Subsequent writes to the file will always end up at the then current end of file, irrespective of any intervening seeks or similar                                                                      |
| t    | File contents interpreted as encoded text strings. The bytes in the file will be encoded and decoded according to the specified text encoding, and universal newline translation will be in effect (unless explicityly disabled). all Methods which write and read data from the file accept and return `str` objects (default) |
| b    | File contents are treated as raw bytes. All methods which write and read data from the file accept and return `bytes` objects                                                                                                                                                                                                   |



## List Comprehensions 
  numbers = [1, 2, 3, 4, 5]
  * List comprehension  
  `[ num*2 for num in numbers] -> outputs a list w/ each number in original * 2`

  * List Comprehension with logic  
  `[ num for num in number if num % 2 == 0] outputs all even numbes from original`  
      *if no else, comprehension comes first, then logic check*
      
      `[ num*2 if num % 2 == 0 else num/2 for num in numbers]`  
    *first result output, logic check, else clause, for clause in comprehension*
    `nested_list = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]`  


  * Nested List Comprehensions  
`  [[val*2 for val in l] for l in nested_list]] output ->`  
  `[[2, 4, 6], [8, 10, 12], [14, 16, 18]]`  
  `[["x" if num % 2 != 0 else "o" for num in range(1,4)] for val in range(1,4)]`
  
## Setting up your environment 

In your project directory, create a 'requirements.txt' file listing
all the modules you need on install and run:  
    
    `pip install -r requirements.txt`

<table>
  <tr>
    <td width='200px'>
    Set Environmental key
    </td>
    <td width='500px'>
    os.environ['name_of_variable'] = 'value of variable'
    </td>
  </tr>
  <tr>
    <td>
    retrieve Environmental key
    </td>
    <td>
    os.getenv('name_of_variable')
    </td>
  </tr>
</table>

## Reading and Writing files  

Modules: pathlib, os  
[Path Module](modules/path)  
[OS Module](modules/os)  


## Working with Excel Spreadsheets 
```
  needed 3rd party module    | openpyxl
                             |
--------------------------------------------------------------------------------
= Python logging library =
  Import                     | import logging
                             |
  setting configuration      | logging.basicConfig(level=logging.DEBUG, filename="log.log", filemode="w",
  and format                 |                     format="%(asctime)s - %(levelname)s - %(message)s")
                             |
  Log Levels                 | logging.debug(f"debug {testval}")
                             | logging.info(f"info {testval}")
                             | logging.warning(f"warning {testval}")
                             | logging.error(f"error {testval}")
                             | logging.critical(f"critical {testval}")
                             |
  Definine custom loggers    | # <-- `__name__` specifies that you are current modules name as the name for this specific logger
                             | logger = logging.getLogger(__name__)
                             |
                             | # Set location and name of log file
                             | handler = logging.FileHandler('test.log')
                             |
                             | # Create the formatter string
                             | formatter = logging.Formatter("%(asctime)s - %(name)s - %(levelname)s - %(message)s")
                             |
                             | # set formatter on handler
                             | handler.setFormatter(formatter)
                             |
                             | # add Handler to logger
                             | logger.addHandler(handler)
                             |
                             | # Now the custom logger will be able to use and log specific log levels
                             | logger.info("Test custom logger")
```

## Modern Python 3 Notes 
### Data types
```
    None (null)              | None  <-- (case sensitive) - (class 'NoneType')
  String interpolation
    format strings (f-string)| f'interpolated data --> {variable/expression}'
                             |
    format method            | 'interpolated data --> {}'.format(<value>)
 ```
### Logical Operators
 ```
    and                      |
    or                       |
    not                      |
 ```
## General Notes 
 ```
  Converting a character to  |
  ascii                      |
                             |
  ord()                      | returns the numerical value of a letter
                             | ord('a') --> 97
                             |
  chr()                      | returns the letter value of a number
                             | char(97) --> 'a'
                             |
  divmod                     | divmod divides two numbers and returns
                             | a tuple containing both the whole value and remander
 ```

## General Class construction 
  [OOP](programmingConcepts/oop)

## Creating a new virtual environment 
  [Virtual Environment](programmingConcepts/virtual_environment)
