> A computer once beat me at chess, but it was no match for me at kickboxing. — Emo Philips

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


NOTE: **After you are done writing a test, always check that it passes and fails when expected.**

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

#### What to automate

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


## Working on a project

When working on a project with multiple people/teams, you should agree on a _way of work_ and have it written down as soon as possible, preferably during your first days on the project.

This should contain info on the test automation process in SDLC (Software Development Life Cycle), such as:

- requesting and verifying the locators needed for test automation
- when the tests are being run
- which tests are run and on which build/environment
- responsibility for checking the test report and reporting bugs

### Requesting IDs

Ideally, if test automation is being done on the project, you should have most of the locators ready. If not, it is important to discuss early on who will be responsible for:

- preparing the locators (how they should look like and which element to put them on)
- opening tasks for developers requesting new locators
- verifying the locators are put on the correct elements

It will usually be the responsibility of a TAE. In case there are multiple TAEs on the project, a dedicated person should be decided on to make the process faster.

A few things to consider when opening a new task:

- task should be short and concise
- better to open a few smaller ones than one big one
- have the tasks logically structured (e.g. per screen or feature)
- add link to the design

When preparing the locators, you should consider a tool that is already being used for design. In case the design is being done in Figma, you could use that one. Not to mess up the design, you should create a separate document which will contain all the screens to which you want locators to be added. Simply copy and paste the screens and using tools like an arrow and a text field, mark the element that needs a locator. Then, when opening a task for the developers, insert the link that points to the screen with marked elements.

When working on locators, it would be wise to have a page with a few examples, a "standardization" of a sort. For example, you want all the buttons to be prefixed with "btn\_" or suffixed with "\_button". The same goes for all other elements like input fields, sliders, etc.

Maybe the developers on the project already have an agreed way of working, so you could continue with that. The idea is to have somewhat similar-looking locators throughout the app.

**NOTE:** A "known issue" is when there are multiple child elements inside a parent element. For example, a LayoutView in Android might have multiple elements. Depending on the functionality, you will probably need a separate locator for each of those child elements. Otherwise, if a locator is put on the LayoutView, you will only get a better-looking XPath on the child elements. Think twice when considering elements which need a locator.

### Version control

Regardless of whether you work as the only TAE on the project or with multiple people, there are some good practices you should follow when naming your git branches.

We can divide them into:

- permanent branches
- temporary branches

#### Permanent branches

Permanent branches will most likely stay in your repository permanently.

**Main** (_master_)

- it should always be stable
- it should be up-to-date
- new code should only be merged after a code review
- should not be used for experimenting with the new code

**Development**

- used for checking the new code
- used for reviews
- gets merged into _main_ after passing a code review

#### Temporary branches

Temporary branches, as the name indicates, are meant to live in the repository temporarily. Before starting work on a new feature or a test, you should check out a new branch. Once you are done with your work, and made sure everything works as expected, you can continue with merging the branch to develop/main after passing the code review.

#### Branch naming

While permanent branches are mostly to be the same on all projects, you will have some more freedom with naming your temporary branches. Branch names should be short yet meaningful.

Often used names, or rather prefixes, are:

- Bugfix
- Hotfix
- Feature
- WIP

To further make clear what is being worked on in a specific branch, you can add a unique ID to the name, as well as a hyphen, underscore and slash. You can even add the author's name in the branch name to further distinguish who is working on which branch.

On whichever method you decide on, make sure to keep using it consistently.

Good branch names:

`wip-4827-add-login-test`

`username_wip_login_tests`

`fix/typos_in_test_data`


Bad branch names:

`bugfix`

`wip_add_test_that_checks_that_the_login_works`

`itisdifficulttoreadthenameofthisbranch`

#### Pull requests (PR)

**Opening a PR:**

- Before diving into doing potential code-breaking changes in the repository, discuss them with your team.
  - E.g., configuration changes should be discussed beforehand.
- Keep PRs small and focused.
  - Focus on a single feature or test suite.
  - Keep configuration changes in a separate PR.
- Split commits into logical sections.
  - Avoid committing a bunch of unrelated files under a single ambiguous commit.
- Write short and meaningful commit messages.
- Add a description why the PR is necessary.

**Reviewing a PR:**

- Strive to review a PR within 24 hours.
- Carefully review the changes.
- Leave clear questions and comments in the appropriate lines of code/files.
- If you have a lot to discuss, consider jumping into a call instead of writing novels in the PR.

[How to handle pull requests without making enemies](https://infinum.com/blog/write-good-pull-requests/)

### Test reports

One of your tasks is to often check the reports generated by test automation.

If there are tests that ended in error or fail, make sure the issue is not in the framework or a mistake in the tests. If the issue is in the app, report it to the QA team for further investigation.
