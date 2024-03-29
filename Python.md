--------------------------------------------------------------------------------
= Python notes =
--------------------------------------------------------------------------------
== Books ==
  [[AtBS|Automate the Boring Stuff]]
--------------------------------------------------------------------------------
== Common Useful commands ==
  [[Python/common_useful_commands|Common useful commands]]
--------------------------------------------------------------------------------
== Common Modules ==
  [[common_modules]]
--------------------------------------------------------------------------------
== Defined Terms ==
  [[programmingConcepts/Terms|Defined Terms]]
--------------------------------------------------------------------------------
== Python built-in Types ==
  [[programmingConcepts/builtins|Built-ins]]
--------------------------------------------------------------------------------
== String Methods ==
  [[programmingConcepts/strings|Strings]]
--------------------------------------------------------------------------------
== List functions ==
  [[programmingConcepts/lists|Lists]]
--------------------------------------------------------------------------------
== Dictionary Methods ==
  [[programmingConcepts/hash-dict|Hash/dictionary]]
--------------------------------------------------------------------------------
== Bult-in Function ==
  [[programmingConcepts/Modules|Modules]]
--------------------------------------------------------------------------------
== exception handling ==
  [[programmingConcepts/Error_handling|Error Handling]]
--------------------------------------------------------------------------------
== Web Scraping ==
  [[Python/web_scraping.wiki|Web Scraping]]
--------------------------------------------------------------------------------
== List Comprehensions ==
  numbers = [1, 2, 3, 4, 5]
  * List comprehension
  [ num*2 for num in numbers] -> outputs a list w/ each number in original * 2

  * List Comprehension with logic
  [ num for num in number if num % 2 == 0] outputs all even numbes from original
    # if no else, comprehension comes first, then logic check

  [ num*2 if num % 2 == 0 else num/2 for num in numbers]
    # first result output, logic check, else clause, for clause in comprehension

`  nested_list = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]`
  * Nested List Comprehensions
  [[val*2 for val in l] for l in nested_list]] output ->
    [[2, 4, 6], [8, 10, 12], [14, 16, 18]]
  [["x" if num % 2 != 0 else "o" for num in range(1,4)] for val in range(1,4)]
--------------------------------------------------------------------------------
== Setting up your environment ==
In your project directory, create a 'requirements.txt' file listing
all the modules you need on install and run:
    pip install -r requirements.txt
                             |
  Set Environmental key      | os.environ['name_of_variable'] = 'value of variable'
  retrieve Environmental key | os.getenv('name_of_variable')
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
--------------------------------------------------------------------------------
=== Reading and Writing files ===
Modules: pathlib, os
[[modules/path|Path Module]]
[[modules/os|OS Module]]
                             |
                             |
                             |
                             |
                             |
--------------------------------------------------------------------------------
=== Working with Excel Spreadsheets ===
  needed 3rd party module    | openpyxl
                             |
                             |
                             |
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
=== Modern Python 3 Notes ===
  Data types
    None (null)              | None  <-- (case sensitive) - (class 'NoneType')
  [[String]] interpolation
    format strings (f-string)| f'interpolated data --> {variable/expression}'
                             |
    format method            | 'interpolated data --> {}'.format(<value>)
                             |
  Logical Operators
    and                      |
    or                       |
    not                      |
--------------------------------------------------------------------------------
=== General Notes ===
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
=== General Class construction ===
  [[programmingConcepts/oop]]
--------------------------------------------------------------------------------
=== Creating a new virtual environment ===
  [[programmingConcepts/virtual_environment]]
                             |
--------------------------------------------------------------------------------
