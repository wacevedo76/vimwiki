# Unittest
## Take Aways
* The unittest module is a framework for developing reliable automated tests.
* You define test cases by subclassing from `unittest.TestCase`.
* The `unittest.main()` function is useful for running all of the tests in a module.
* The `setup()` and `tearDown()` fixtures are used to run code before and after each test method.
* The various `TestCase.assert`... methods can be used to make a test method fail when the right conditions aren't met
* Use `TestCase.assertRaises()` in a with-statement to check that the right exceptions are thrown in a test
