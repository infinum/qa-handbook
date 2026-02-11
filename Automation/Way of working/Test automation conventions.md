## Frameworks

Keep your framework lightweight. It should be easy to get around, easy to understand, and easy to maintain.

In practice, a lightweight framework usually means:

- a small number of custom abstractions and wrappers
- clear entry points (where tests start, where configuration and fixtures live)
- failures that are easy to debug from the test output and logs

Signals that the framework is becoming too complex:

- adding a new simple test requires touching many files in unrelated places
- most failures need you to step through multiple layers of wrappers to understand what really happened
- new team members struggle to find “where things start” or “where to add a new test”

A short `README` or onboarding document that explains the main folders and how to run a subset of tests is a must.

## Project structure

When working on UI automation, a design pattern such as Page Object Model (POM) should be used when structuring the project. Similar ideas (separating concerns, centralizing access to external systems) can be applied to other types of automated tests as well.

With POM implemented:

- the readability of tests is improved
- it is easier to understand which parts of the UI are covered and how
- the impact of changes is clearer (you usually update a single page object instead of many tests)
- the overall maintenance of the project is easier

### Page objects

Page objects should only contain locators for that specific page/screen.

Read the [locators article](https://infinum.com/handbook/qa/automation/locators/general) for more details on using locators.

Methods related to those locators should also be located on the same page as the locators they are using. The structure can be further split by separating methods into a separate class, e.g. suffixed by _"\_actions"_. That class should only contain methods related to the screen (or feature) they refer to.

The exception are locators and actions that are shared across multiple pages, such as dialog windows. Those can be in their own class.

Avoid adding assertions or complex business rules inside page objects. Page objects should describe how to interact with the UI (click, type, read values), while tests decide what to verify and what the expected behavior is.

### Tests

Tests should be:

- easy to understand
- easy to maintain
- independent of other tests

**NOTE:**

- After you are done writing a test, always check that it passes and fails when expected.

#### Independent tests

Ideally, you want to write independent tests.

Independent tests:

- do not depend on other tests or test suites
- can run in any order
- can easily run in parallel

However, you might not be able to follow _best practices_ on every single project.

When considering the difference between a web and a mobile project, it is obvious the way the apps work is different. While on a web page you can often jump directly to a specific URL, on a mobile app you usually have to follow a certain flow before getting to the desired screen.

Something worth considering is the time it takes for the tests to run and the cost of test automation. By adding more tests, the more time it will take for them to run. If you need real hardware for your tests and you are limited by the number of devices you have, your test suite will not scale easily. Additionally, preparing the initial state for a test might take too much time. If each test needs 10 minutes of setup before it even reaches the part you want to check, you might not be able to run many tests in a desirable amount of time.

To keep tests as independent as possible, especially on mobile, consider:

- using deep links or navigation shortcuts when available, instead of tapping through long flows
- setting up data via APIs, database, or fixtures instead of creating it through the UI in every test
- resetting state between tests (log out, clear app data, reset test user) so each test starts from a known state

Sometimes it still makes sense to have a “flow” test suite that intentionally follows a long user journey end to end (e.g., onboarding or checkout). In those cases, treat that suite as a smaller group of slower tests and keep the majority of your tests independent.

#### What to automate?

Be careful not to fall into a trap of just adding tests to report back the number of newly added ones. Having a lot of tests does not mean we are doing it right.

After a few months or years on the project, you might end up with hundreds of tests, if not more. If you just keep adding more tests without being careful about their stability, they will become harder to maintain. If you make a few mistakes along the way, those mistakes might pile up and be impossible to fix at some point. Some tests might just be too difficult to automate and not bring any value. Others might be flaky and ask for more time to maintain them than it took to write them.

Questions worth asking before/during test automation:

- What will we achieve by having 10000000 automated tests?
- Do they bring us any value?
- How stable are the tests?
- Which functionalities to cover with automated tests?
- Which/how many scenarios to add (positive, negative, a few extra ones)?

A short checklist to evaluate whether a scenario is a good candidate for automation:

- **Business impact**: Does this flow matter to users or revenue (for example, sign-up, login, payment)?
- **Change frequency**: Does the functionality change often? Very unstable UI or copy might be better covered by manual tests.
- **Flakiness risk**: Does the scenario depend on many external systems (payment providers, third-party APIs, external emails)? If yes, consider isolating those parts or using contracts/mocks.
- **Observability**: Will you be able to understand failures quickly from logs, screenshots, and test reports?
- **Run time**: Can the test run within a reasonable time on your CI and local machines?

As a rule of thumb:

- automating a critical “happy path” (e.g., successful checkout) usually brings high value
- automating very detailed and frequently changing visuals (e.g., exact pixel distances, color shades) often does not

When starting with test automation, the focus should be on:

- regression testing
- smoke/sanity testing

Afterwards, depending on the project or when you cover all the existing features, you could continue with covering new functionalities.

#### Flaky tests

At some point, you will write a test that works okay for a while, but then it starts misbehaving — sometimes passes, and then sometimes fails.

Before you delete a flaky test, try the following:

- check whether the failure is caused by timing issues and wait for stable conditions instead of using fixed sleeps
- simplify or improve locators so the test interacts with the correct elements
- decouple the test from unstable external dependencies by using test accounts, mock services, or test data that changes less often

If you end up updating and tweaking the test every once in a while and simply cannot get it to work properly, consider removing that test. Otherwise, it will only cause you headaches and take up the time that you could have spent better.

Maybe it should simply be tested manually.

### Asserts

In test automation, assertion is the validation step that determines whether the automated test case was successful or not. Every test should have at least one assert through which we confirm that the actual result matches the expected one.

Don't reinvent the wheel when it comes to assertions. There are a bunch of assertion libraries that can be used out of the box. Don't write your own verification methods unless it's really necessary.

Some general conventions that help keep asserts useful:

- prefer a single main assert per test scenario, focused on the primary outcome you care about
- add additional asserts only when they help you understand failures better or validate important side effects
- use clear assertion messages so that failures are easy to understand from the report alone

When asserting results in failure, the test execution is usually aborted. However, sometimes you do not want to abort the test but let it finish. Therefore, it is important to know about the difference between types of assertions.

#### Hard assert

Hard asserts refer to asserts that stop the test execution in case of an assertion error. In case you put an assertion in the middle of the test, this is where the test stops.

This type of assert should be used when you do not want the test to continue since the condition for further steps might not have been met. For example, you need to have a user created before continuing to the next screen/page. If the user is not created, there is no point in continuing with the tests. The test should be marked as _fail_.

#### Soft assert

Soft asserts refer to asserts that do not stop the test execution in case of an unexpected result. This type of assert is also useful because you can have multiple asserts throughout the test. The test execution will not stop if any of the asserts fail. When the test comes to an end, you will get the result on all failed asserts.

For example, you have a screen with a list of values that you want to check, but those values are not a precondition to any of the following steps. If any of the values are incorrect, it will not affect the following steps. You can simply add as many soft asserts as there are values on the screen and check that all of them match the expected result.

One difference compared to hard asserts is that, in some libraries, you have to collect all soft asserts at the end of the test. Otherwise, the asserts are not evaluated.

Example using [pytest-check](https://pypi.org/project/pytest-check/) (Python):

```python
import pytest_check as check


def test_example_one():
    # First assert
    check.is_in("a", "car")

    # Second assert
    check.is_equal("username", "username")
```

Example using [softest](https://pypi.org/project/softest/) (Python):

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
