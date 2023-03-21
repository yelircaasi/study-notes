# Pytest

[Docs](https://docs.pytest.org/en/7.2.x/)

## Python Testing with pytest

### 1. Getting Started with pytest

--tb=no turns off traceback

possible to run just a file, multiple files, or just the files
in one directory, by passing these as command-line argument(s)

discoverability of tests:

* files: test_*.py or *_test.py
* functions: test_*()
* classes: Test*

possible test outcomes:

* . - passed
* F - failed
* s - skipped
* x - xfail
* X - xpass
* E - error

## 2. Writing Test Functions

`__tracebackhide__` variable for assertion helper functions

`pytest.fail()`

`--tb=short` can also be nice

Arrange-Act-Assert ~ Given-When-Then: pattern for separating a test
into stages: starting state, then some action to perform, then assertion

## 3. pytest Fixtures

`--setup-show` can be used to trace fixtures

`conftest.py` can be at any level of the test directory

multiple fixture levels makes tests much cleaner,
as in the database example

hook functions allow new command-line arguments

notes from the chapter summary:

* Fixtures are @pytest.fixture() decorated functions.
* Test functions or other fixtures depend on a fixture by putting its name in
  their parameter list.
* Fixtures can return data using return or yield.
* Code before the yield is the setup code. Code after the yield is the
  teardown code.
* Fixtures can be set to function, class, module, package, or session scope.
  The default is function scope. You can even define the scope dynamically.
* Multiple test functions can use the same fixture.
* Multiple test modules can use the same fixture if it’s in a conftest.py file.
* Multiple fixtures at different scope can speed up test suites while
  maintaining testisolation.
* Tests and fixtures can use multiple fixtures.
* Autouse fixtures don’t have to be named by the test function.
* You can have the name of a fixture be different than the fixture function name.
* pytest --setup-show is used to see the order of execution.
* pytest --fixtures is used to list available fixtures and where the fixture
  is located.
* -s and --capture=no allow print statements to be seen even in passing tests.
