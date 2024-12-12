## Pytest
### Running Test in Pytest
  * Pytest can be run in several different ways:
    * `pytest`: With no arguments, pytest searches the local directory and subdirectories for tests.
    * `pytest <filename>`: Runs the tests in one file.
    * `pytest <filename> <filename>`: Runs the tests in multiple named files.
    * `pytest <dirname>`: Stars in a particular directory and recursively searches for tests.  
### Naming Conventions
* Test discovery referes to how pytest finds your test code and depends on naming:

| Purpose      | Convention                                     |
| -------      | ----------                                     |
| Test Files   | `test_<something>.py` or `<something>_test.py` |
| Test Methods | `test_<something>`                             |
| Test Classes | `Test<Something>`                              |
### Command line flags

| Purpose                               | Note                       |
| -------                               | ----                       |
| Verbose                               | `-v`, `--verbose` or `-vv` |
| Print test results without tracebacks | `--tb=no`                  |
| Specify a test function within a test | `test_file.py::test_name`  |
### Test Outcomes

| Outcome     | Purpose                                                                                                                           |
| -------     | -------                                                                                                                           |
| PASSED (.)  | The test rand successfully                                                                                                        |
| FAILED (F)  | The test did not run successfully                                                                                                 |
| SKIPPED (s) | The test was skippped (`@pytest.mark.skip()` or `@pytest.mark.skipif()`)                                                          |
| XFAIL (x)   | The test was not supposed to pass, and it ran and failed (`@pytest.mark.xfail()`)                                                 |
| XPASS (X)   | The test was marked with xfail, but it ran and passed                                                                             |
| ERROR (E)   | An exception happened either during the execution of a fixture or hook function, and not during the execution of a test function. |

### Assert Statements
  * `assert something`
  * `assert not something`
  * `assert a == b`
  * `assert a !- b`
  * `assert a is None`
  * `assert a is not None`
  * `assert a <= b`
