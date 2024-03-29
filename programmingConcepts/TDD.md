--------------------------------------------------------------------------------
= TDD =
--------------------------------------------------------------------------------
=== Usefult TDD Concepts ===
  User Story
    A description of how the application will work from the point of view of the
    user.
    Used to structure a function test.

  Expected failure
    When a test fails in the way that we expected it to.

  Regression
    When new code breaks some aspect of the application which used to work.

  Unexpected failure
    When a test fails in a way we weren't expecting. This either means that we've
    made a mistake in our tests, or that the tests have helped us find a regression,
    and we need to fix something in our code

  Red/Green/Refactor
    Another way of describing the TDD process. Write a test and see it fail (Red),
    write some code to get it to pass (Green), then Refactor to improve the
    implementation

  Triangulation
    Adding a test case with a new specific example for some existing code, to
    justify generalizing the implementation (which may be  a "cheat" until that point.)

  Three strikes and refactor
    A rule of thumb for when to remove duplication from code. When two pieces of
    code look very similar, it often pays to wait until you see a third use case,
    so that you're more sure about what part of the code really is the common,
    re-usable part to refactor out.

  The scratchpad to-do list
    A place to write down things that occur to us as we're coding, so that we can
    finish up what we're doing and come back to them later.

  Ensuring test isolation and managing global state
    Different tests shouldn't affect one another. This means we need to reset any
    permanent state at the end of each test. Django's test runner helps us do this
    by creating a test database, which it wipes clean in between each test.

  Avoid "voodoo" sleeps
    Whenever we need to wait for something to load, it's always tempting to throw
    in a quick-and-dirty time.sleep. But the problem is that the length of time we
    wait is always a bit of a shot in the dark, either too short and vulnerable to
    spurious failures, or too long and it'll slow down our test runs. Prefer a
    retry loop that polls our app and moves on as soon as possible

  Don't rely on Selenium's implicit waits
    Selenium does theoretically do some "implicit" waits, but the implementation
    varies between browser,s and at the time of writing was highly unreliable in
    the Selenium 3 Firefox driver. "Explicit is better than implicit", as the Zen
    of Python says, so prefer explicit waits
--------------------------------------------------------------------------------
== Functional Tests vs Unit Tests ==
--------------------------------------------------------------------------------
Overall TDD Process
  Functional Test - Desscribing the new functionality from the user's poine of view
  Unit Test - define how we want the code to behave.
--------------------------------------------------------------------------------
1. Write a test
2. Run the test -> does it pass?
  YES -> Does it need refactoring?
    YES -> Write minimal code
    NO -> Write a (new) test
  NO -> Write minimal code
--------------------------------------------------------------------------------
== Python's Unittest module ==
--------------------------------------------------------------------------------
From Python's documentation - Unittest module basic parts
import unittest

class TestStringMethods(unittest.TestCase):     <-- Class definition
                                                    inherits from unittest.Testcase
    def setUp(self):                            <-- Define setup code
        self.widget = Widget('The widget')

    def tearDown(self):                       <-- Define code to clean up setup code
        self.widget.dispose()

    def test_upper(self):
        self.assertEqual('foo'.upper(), 'FOO')  <-- standard assert for Equality

    def test_isupper(self):
        self.assertTrue('FOO'.isupper())        <-- assert for Boolean (True)
        self.assertFalse('Foo'.isupper())       <-- assert for Boolean (False)

    def test_split(self):
        s = 'hello world'
        self.assertEqual(s.split(), ['hello', 'world'])
        # check that s.split fails when the separator is not a string
        with self.assertRaises(TypeError):      <-- assert for thrown error
            s.split(2)

    def test_fail(self):
        self.fail('Finish the test!')           <-- will force a test fail

if __name__ == '__main__':
    unittest.main()
--------------------------------------------------------------------------------
=== Python Test Fixtures ===
import unittest

def setUpModule():
    """called once, before anything else in this module"""
    print("In setUpModule()...")

def tearDownModule():
    """called once, after everything else in this module"""
    print("In tearDownModule()...")

class TestClass06(unittest.TestCase):

    @classmethod
    def setUpClass(cls):
        """called once, before any test"""
        print("In setUpClass()...")

    @classmethod
    def tearDownClass(cls):
        """called once, after all tests, if setUpClass successful"""
        print("In tearDownClass()...")

    def setUp(self):
        """called multiple times, before every test method"""
        print("\nIn setUp()...")

    def tearDown(self):
        """called multiple times, after every test method"""
        print("\nIn tearDown()...")

    def test_case01(self):
        self.assertTrue("PYTHON".isupper())
        print("In test_case01()")

    def test_case02(self):
        self.assertTrue("python".isupper())
        print("In test_case02()")

if __name__ == '__main__':
    unittest.main()

---- Output from code ----------------------------------------------------------

In setUpModule()...
In setUpClass()...
test_case01 (__main__.TestClass06) ...
In setUp()...
In test_case01()

In tearDown()...
ok
test_case02 (__main__.TestClass06) ...
In setUp()...

In tearDown()...
FAIL
In tearDownClass()...
In tearDownModule()...

======================================================================
FAIL: test_case02 (__main__.TestClass06)
--------------------------------------------------------------------------------
=== unittest module Notes: ===
  1. Tests are organized into classes, which inherit from unittest.TestCase
  2. The main body of the test is in a method call "test_upper". Any method whose
     name starts with 'test' is a test method, and will be run by the test runner
  3. 'setUp' and 'tearDown' are special methods which get run before and after
     each test.
  4. 'self.assertIn' is one of many help functions to make assertions.
     'assertEqual', 'assertTrue', 'asertFalse' are some other common assertions
  5. self.fail just fails no mater what, producting the error message given
  6. if __name__ == '__main__' clause -> used to check if the script has been
     executed or just imported by another script. When unittest.main() is called
     it launches the unittest test runner, which automatically finds test classes
     and methods in the file and runs them.
--------------------------------------------------------------------------------
