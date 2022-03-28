> A computer once beat me at chess, but it was no match for me at kickboxing. — Emo Philips

## General

### Basic principles

- Tests should be easy to write

- Tests should be easy to understand

- Tests and test suites should be easy to maintain

- Tests should help testers with quality assurance


### What is the benefit of test automation?

- Reduce regression time

- Gives testers more time to focus on more complex scenarios and to do exploratory testing

- Automated test can run more quickly through tedious scenarios using various input


### What test automation is not

Test automation is not here to replace testers completely.
It is to be used primarily to help testers to test the app more thoroughly in shorter amount of time.

However, the idea is not to automate every single scenario but to focus on scenarios that will benefit us.


### Philosophy

- You shouldn’t have to recompile your app or modify it in any way in order to automate it

- You shouldn’t be locked into a specific language or framework to write and run your tests

- A mobile automation framework shouldn’t reinvent the wheel

- A mobile automation framework should be open source, in spirit and practice as well as in name


## Frameworks

Keep your framework lightweight. 
It should be easy to get around, easy to understand and maintain the framework.


## Project structure

A design pattern such as Page Object Model (POM) should be used when structuring the project.

With POM implemented:

- it is easier to get around

- the readability is improved

- the overall maintenance of the project is easier


### Page objects

Page objects should only contain locators for that specific page / screen.

Read the [locators article](https://infinum.com/handbook/qa/automation/locators) for more details on using locators.

Methods related to those locators should also be located on the same page as the locators they are using.
The structure can be further split by separating methods into a separate class suffixed by "_actions". That class should only contain methods related to the screen they refer to.

The exception are locators and actions that are shared across multiple pages, such as dialog windows. Those should then be in their own class.


### Tests

WIP



NOTE:
After you are done writing a test, always make sure to check that it passes and fails when expected.


#### What to automate

Probably starting from day one, management will ask you: 
- how many test cases can you write?
- how many tests do we have?

We should **not** just blindly automate as many tests as possible. Some tests take too much time to automate, some end up being flaky, some are just too difficult to automate.
Then after a few months / years on the project, you end up having hundreds of tests, if not more. If you just keep adding more tests, they will become harder to maintain.
If you make a few mistakes along the way, those mistakes might look impossible to fix at some point.


- What will we achieve by having 10000000 automated tests?
- Do they bring us any value?
- How stable are those tests?
- Which functionalities to cover with automated tests
- Which / how many scenarios to add (positive, negative, a few extra ones?)

Focus:

- regression testing
- smoke / sanity testing

#### Flaky tests

At some point, you will write a test that looks ok, and works ok for a while, but then it starts misbehaving. Sometimes passes, and then sometimes fails.
If you end up updating and tweaking the test every once in a while and simply cannot get it working properly, consider removing that test. 
Otherwise, it will only cause you headache, take up your time that could have been spent better, and mess up the report. Maybe it should simply be tested manually.


### Asserts

In test automation, assertion is the validation step that determines whether the automated test case was successful or not.
Every test should have at least one assert through which we confirm that the actual result matches the expected one.

Don't reinvent the wheel when it comes to assertions. There are a bunch of assertion libraries that can be used out-of-the box.
Don’t write your own verification methods unless it's really necessary.

When assert results in failure, the test execution is usually aborted. However, sometimes you do not want to abort the test but let it finish.
Therefore, it is important to know about difference between types of assertions. 

#### Hard asserts

Hard asserts refer to asserts that stop the test execution in case of an Assertion Error.
In case assert has been put in the middle of the test, this is where the test stops.

This type of assert should be used when you do not want the test to continue since the condition for further steps might not have been met.
For example, you need to have a user created before continuing to the next screen / page. If the user is not created, there is no point in continuing with the tests. The test should be marked as fail.


#### Soft asserts

Soft asserts refer to asserts that do not stop the test execution in case of an unexpected result.
This type of asserts are also useful since you can have more than one. 

You can hace multiple asserts throughout the test. The test will not fail if any of the asserts fail.
When the test comes to an end, you will get the result on all asserts that failed.

For example, you have a screen with a list of values that you want to check, but those values are not a precondition to any of the following steps. If any of the values are incorrect, it will not affect the following steps.
You can simply add as many soft asserts as there are values on the screen and check all of them match the expected result.

One difference compared to the hard assert is that you will usually have to collect all the soft asserts at the end of the test. Something which is not needed for the hard assert.

Example using [softest](https://pypi.org/project/softest/):

```
// First assert
self.soft_assert(self.assertEqual, found_title, expected_title)

// Second assert
self.soft_assert(self.assertEqual, found_subtitle, expected_subtitle)

// Collect all asserts
self.assert_all()
```


## Working on a project

When working on a project with multiple teams, you should agree on a _way of work_ and have it written down. 

This should contain info on automation process in SDLC, such as:

- requesting and verifying the locators needed for test automation
- when are the tests being run
- which tests are run and on which build
- responsibility of checking the test report and reporting bugs




### Requesting IDs

Sometimes multiple people, even teams, might be working on test automation. Having a dedicated person(s) will make the process much faster.

Before preparing the workflow for requesting and maintaining locators, it would be wise to have adding locators a part of the acceptance criteria.
For starters, while developing new features, the developers should add locators at least on all input fields and buttons. On other elements that might be used in test automation, the locators can be added later on.

It is important to discuss early on who will be responsible for:
- preparing the locators (how should they look like and on which element to put them on)
- opening tasks for developers requesting new locators 
- verifying the locators are put on the correct elements

One thing to consider when opening a new task:
- task should be short and concise
- better to open a few smaller ones than one huge one
- have the tasks logically structured (e.g. per screen or feature)
- add link to design 

When preparing the locators, you should consider a tool that is already being used for design. In case the design is being done in Figma, you could use that one. 
Not to mess up the design, you should create a separate document which will contain all the screens to which you want locators to be added.
Simply copy and paste the screens and using tools like an arrow and a text field, mark the element that needs a locator.
Then, when opening a task for the developers, insert the link that points to the screen with marked elements.

When working on locators, it would be wise to have a page with a few examples, a "standardization" of sort.
For example, you with all the buttons to be prefixed with "btn" or suffixed with "_button".
The same goes for all other elements like input fields, sliders, etc.

Maybe the developers on the project already have an agreed way of working so you could continue with that. The idea is to have a somewhat similar looking locators throughout the app.

**NOTE:**
A "known issue" is when there are multiple child elements inside a parent element. 
For example, a LayoutView in Android might have multiple elements. Depending on the functionality, you will probably need a separate locator for each of those child elements.
Otherwise, if a locator is put on the LayoutView, you will only get a better looking Xpath on the child elements.
Think twice when considering elements which need a locator.



---


![dilbert_automation_wow.png](/img/dilbert_automation_wow.png)

*Image downloaded from [dilbert.com](https://dilbert.com/strip/2012-04-09) by Scott Adams*
