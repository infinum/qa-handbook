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



### Page objects



### Tests



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

// First assert

`self.soft_assert(self.assertEqual, found_title, expected_title)`

// Second assert

`self.soft_assert(self.assertEqual, found_subtitle, expected_subtitle)`

// Collect all asserts

`self.assert_all()`


---


![dilbert_automation_wow.png](/img/dilbert_automation_wow.png)

*Image downloaded from [dilbert.com](https://dilbert.com/strip/2012-04-09) by Scott Adams*
