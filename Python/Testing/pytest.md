## Pytest
### Chapter 1 Review:  
  * Pytest can be run in several different ways:  
    * `pytest`: With no arguments, pytest searches the local directory and subdirectories for tests.
    * `pytest <filename>`: Runs the tests in one file.
    * `pytest <filename> <filename>`: Runs the tests in multiple named files.
    * `pytest <dirname>`: Stars in a particular directory and recursively searches for tests.  
 <br> 
  * Test discovery referes to how pytest finds your test code and depends on naming:  

  * Test files should be named `test_<something>.py` or `<something>_test.py`.  
    * Test methods and functions should be named `test_<something>`.
    * Test classes should be named `Test<Something>`.  
 <br> 
  * The possible outcomes of a test function include:  
    * PASSED (.)
    * FAILED (F)
    * SKIPPED (s)
    * XFAIL (x)
    * XPASS(X)
    * ERROR (E)  
 <br> 
  * The `-v` or `--verbose` command-line flag is used to reveal more verbose output.
  * The `--tb=no` command-line flag is used to turn off tracebacks

### Assert Statements
  * `assert something`
  * `assert not something`
  * `assert a == b`
  * `assert a !- b`
  * `assert a is None`
  * `assert a is not None`
  * `assert a <= b`
