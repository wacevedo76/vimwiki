--------------------------------------------------------------------------------
# Python notes
## Books 
[Automate the Boring Stuff](AtBS)  

## Misc
[Common useful commands](Python/common_useful_commands)  
[Common Modules](common_modules)  
[Defined Terms](programmingConcepts/Terms)  
[Built-ins](programmingConcepts/builtins)  
[Strings](programmingConcepts/strings)  
[Lists](programmingConcepts/lists)  
[Hash/dictionary](programmingConcepts/hash-dict)  
[Modules](programmingConcepts/Modules)  
[Error Handling](programmingConcepts/Error_handling)  
[Web Scraping](Python/web_scraping.wiki)  
[Testing](Python/Testing/unittest)  
[Bitwise Operators](Python/bitwise)
[pdb](Python/pdb)


## Reading and writing to files

<table>
  <tr>
    <td>
      Read all data from a file object                   
    </td>
    <td>
      fo.read()  
    </td>
  </tr>
  <tr>
  <td>
    Only read a specific numer of characters             
  </td>
  <td>
    fo.read(32)
  </td>
  </tr>
  <tr>
    <td>More the file pointer to the beginning of the file </td>
    <td>fo.seek(0</td>
  </tr>
  <tr>
    <td width='200px'>Read one line at a time</td>
    <td>fo.readline</td>
  </tr>
  <tr>
    <td>Return a list of all the lines of a file</td>
    <td>fo.readlines</td>
  </tr>
  <tr>
    <td>Write multiple lines</td>
    <td>fo.writelines()</td>
  </tr>
  <tr>
  <td>*With-blocks*</td>
  <td width='500px'>with open(filename, mode='rt', encoding='utf-8') as f:<br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return [int(line.strip()) for line in f]</td>
  </tr>
  <tr>
  </tr>
</table>
  
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
                             |
--------------------------------------------------------------------------------
## Modern Python 3 Notes 
  Data types
    None (null)              | None  <-- (case sensitive) - (class 'NoneType')
  String interpolation
    format strings (f-string)| f'interpolated data --> {variable/expression}'
                             |
    format method            | 'interpolated data --> {}'.format(<value>)
                             |
  Logical Operators
    and                      |
    or                       |
    not                      |
--------------------------------------------------------------------------------
## General Notes 
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
                             |
--------------------------------------------------------------------------------
## General Class construction 
  [OOP](programmingConcepts/oop)
--------------------------------------------------------------------------------
## Creating a new virtual environment 
  [[programmingConcepts/virtual_environment]]
                             |
--------------------------------------------------------------------------------
