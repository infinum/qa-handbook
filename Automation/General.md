> Quality is the ally of schedule and cost, not their adversary. - James A. Ward

## The benefits of test automation

- Helps testers test the app more thoroughly in a shorter amount of time
- Gives testers more time to focus on more complex scenarios and to do exploratory testing
- Automated tests run more quickly through tedious scenarios using various input
- Reduces regression testing time

## What test automation is not

- Test automation is not here to replace testers completely
- The idea is not to automate every single scenario (especially when considering UI tests), but to focus on scenarios that will benefit the project

## Basic principles

- Tests should be easy to write
- Tests should be easy to understand
- Tests and test suites should be easy to maintain
- Tests should help testers with quality assurance

## What to test

Test automation is done on several levels represented by the test pyramid.

Read up on the test pyramid [here](https://martinfowler.com/articles/practical-test-pyramid.html).

![test-pyramid.png](/img/test-pyramid.png)

**UI testing**

UI automation entails writing a test script which will perform the same actions a human tester would on a particular piece of finished/built software.

There are plenty of tools available, but generally there are two approaches:

- Using a test framework and implementing tests by coding them.
- Using a test recorder which will record and play your actions.

You can code and run your tests using just a text editor or an actual IDE which will help you organize your tests and test data, connect to bug tracking systems, etc.

One thing to keep in mind is that the UI tests are the slowest kind of tests. You should think twice when considering which UI tests to automate.
Start with the most important tests that will help the QA team and reduce the regression time.

**API testing**

As seen in the testing pyramid, the API is a connecting (integration) layer.

API tests are fast since there is no UI involved and can quickly verify the communication between software components.
A tool like Postman would be enough to start with API testing right away.

**Unit testing**

Unit tests are the fastest kind of tests, and we should strive to have as many of those as possible.

Since writing them requires being familiar with the codebase, they are written and maintained by developers.

## Tools

### Web frameworks - Selenium

[Selenium](https://www.selenium.dev/) is probably the most popular web automation framework built on top of WebDriver (as many others are). We use it for web UI automation.

Selenium IDE was developed for testers and developers to record their actions as they follow the workflow that they need to test.

There are plenty of competing tools and frameworks out there. To name a few:

- [Cypress](https://www.cypress.io/)
- [WebdriverIO](https://webdriver.io/)
- [Puppeteer](https://github.com/puppeteer/puppeteer)
- [Playwright](https://github.com/microsoft/playwright)

### Mobile frameworks - Appium

Selenium's mobile analogue, used for automating hybrid and native mobile apps. We use it for mobile UI automation.

**Appium is:**

- an open-source automation tool
- cross-platform (Android, iOS, others)
- used for testing hybrid and native apps
- runs on simulators (iOS) or emulators (Android)
- runs on real devices (iOS, Android)

**Philosophy**

- You shouldn’t have to recompile your app or modify it in any way in order to automate it
- You shouldn’t be locked into a specific language or framework to write and run your tests
- A mobile automation framework shouldn’t reinvent the wheel when it comes to automation APIs
- A mobile automation framework should be open source, in spirit and practice as well as in name

**How does it do it?**

- Uses the WebDriver API,
- uses vendor-provided automation frameworks (UIAutomation on iOS, UiAutomator on Android),
- wraps the vendor-provided framework in the WebDriver API (Selenium WebDriver)
- which specifies a REST client-server protocol (JSON Wire).
- The server is written in Node.js.

**Advantages**

- Write tests using WebDriver-compatible languages which support Appium's extensions: Java, Ruby, Python, JavaScript, C#
- Use any testing/execution framework since Appium is an automation library, not a framework.
- Has an inspector for viewing UI elements.


### Testing API

A great tool to start with API testing is Postman. You can easily pick up the basics and start testing the API right away.
Postman can be used in manual testing, but also offers a few options for automation.

For more info read the [Using Postman](https://infinum.com/handbook/qa/tools/using-postman) article.

**What to test**

When it comes to API there are quite a few details that need checking.
Unfortunately, oftentimes only the status code is being checked. However, especially nowadays with apps doing wonders, that won't cut it.

A few basic things to check:

- status code (all that apply, not only 200)
- response payload
- response headers

Read the [REST API Testing Strategy](https://www.sisense.com/blog/rest-api-testing-strategy-what-exactly-should-you-test/) article for more ideas on what to check.


---

![ui-test-automation.gif](/img/ui-test-automation.gif)
