## Frameworks

Keep your framework lightweight. It should be easy to get around, easy to understand and maintain the framework.


## Project structure

A design pattern such as Page Object Model (POM) should be used when structuring the project.

With POM implemented:

- the readability is improved
- it is easier to understand the project structure
- the overall maintenance of the project is easier


### Page objects

Page objects should only contain locators for that specific page/screen.

Read the [locators article](https://infinum.com/handbook/qa/automation/locators/general) for more details on using locators.

Methods related to those locators should also be located on the same page as the locators they are using. The structure can be further split by separating methods into a separate class, e.g. suffixed by _"\_actions"_. That class should only contain methods related to the screen (or feature) they refer to.

The exception are locators and actions that are shared across multiple pages, such as dialog windows. Those can be in their own class.


### Tests

Tests should be:

 - easy to understand
 - easy to maintain
 - independent of other tests


NOTE:
- **After you are done writing a test, always check that it passes and fails when expected.**


#### Independent tests

Ideally, you want to write independent tests.

Independent tests:

- do not depend on other tests or test suites
- can be run in any order
- can easily be run in parallel (running tests on multiple devices at the same time)

However, you might not be able to follow _best practices_ on every single project.

When considering the difference between a web and a mobile project, it is obvious the way the apps work is different. While on a web page you can easily jump between URLs (most of the time), on a mobile app you have to follow a certain flow before getting to the desired screen.

Something worth considering is the time it takes for the tests to run and the cost of test automation. By adding more tests, the more time it will take for them to run. Also, what if you need real hardware for your tests, and you are limited by the amount of devices you have but there is no budget to get more? Additionally, those devices can only be connected to one mobile device at the time. Furthermore, to prepare the initial state for a test might take too much time. If it takes just 10 min for each test to come to a desired state before continuing, and the steps the tests checks even longer, you might not be able to have many tests run in a desirable amount of time.

In that case, think twice before you start with test automation and discuss with the team what the best approach would be.


#### What to automate?

Be careful not to fall into a trap of just adding tests to report back the number of newly added ones. Having a bunch of tests does not mean we are doing it right. We should **not** just blindly automate everything.

After a few months/years on the project, you will have hundreds of tests, if not more. If you just keep adding more tests without being careful of their stability, they will become harder to maintain. If you make a few mistakes along the way, those mistakes might pile up and be impossible to fix at some point. Some tests might just be too difficult to automate and not bring any value. Others might be flaky and ask for more time to maintain them than it was writing them.

Questions worth asking before/during test automation:

- What will we achieve by having 10000000 automated tests?
- Do they bring us any value?
- How stable are the tests?
- Which functionalities to cover with automated tests?
- Which/how many scenarios to add (positive, negative, a few extra ones)?

When starting with test automation, the focus should be on:

- regression testing
- smoke/sanity testing

Afterwards, depending on the project or when you cover all the existing features, you could continue with covering new functionalities.


#### Flaky tests

At some point, you will write a test that looks okay and works okay for a while, but then it starts misbehaving - sometimes passes, and then sometimes fails.
If you end up updating and tweaking the test every once in a while and simply cannot get it working properly, consider removing that test.
Otherwise, it will only cause you headaches, take up your time that could have been spent better, and mess up the report.

Maybe it should simply be tested manually.


### Asserts

In test automation, assertion is the validation step that determines whether the automated test case was successful or not. Every test should have at least one assert through which we confirm that the actual result matches the expected one.

Don't reinvent the wheel when it comes to assertions. There are a bunch of assertion libraries that can be used out of the box. Don't write your own verification methods unless it's really necessary.

When asserting results in failure, the test execution is usually aborted. However, sometimes you do not want to abort the test but let it finish. Therefore, it is important to know about the difference between types of assertions.


#### Hard assert

Hard asserts refer to asserts that stop the test execution in case of an assertion error. In case you put an assertion in the middle of the test, this is where the test stops.

This type of assert should be used when you do not want the test to continue since the condition for further steps might not have been met. For example, you need to have a user created before continuing to the next screen/page. If the user is not created, there is no point in continuing with the tests. The test should be marked as _fail_.


#### Soft assert

Soft asserts refer to asserts that do not stop the test execution in case of an unexpected result. This type of assert is also useful because you can have multiple asserts throughout the test. The test execution will not stop if any of the asserts fail. When the test comes to an end, you will get the result on all failed asserts.

For example, you have a screen with a list of values that you want to check, but those values are not a precondition to any of the following steps. If any of the values are incorrect, it will not affect the following steps. You can simply add as many soft asserts as there are values on the screen and check that all of them match the expected result.

One difference compared to hard asserts is that, in some libraries, you have to collect all soft asserts at the end of the test. Otherwise, the asserts are not evaluated.

Example using [pytest-check](https://pypi.org/project/pytest-check/):

```python
import pytest_check as check


def test_example_one():
    # First assert
    check.is_in("a", "car")

    # Second assert
    check.is_equal("username", "username")
```

Example using [softest](https://pypi.org/project/softest/):
 
```python
import softest


def test_example_two():
    # First assert
    self.soft_assert(self.assertIn, "a", "car")
 
    # Second assert
    self.soft_assert(self.assertEqual, "username", "username")
 
    # Collect all asserts
    self.assert_all()
 ```
