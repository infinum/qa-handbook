> *Quality is the ally of schedule and cost, not their adversary.*

## General

This section is just a short primer on UI test automation. More will be covered in the following sections on [Web test automation](https://infinum.com/handbook/books/qa/tools/ui-automation-web) and [Mobile test automation](https://infinum.com/handbook/books/qa/tools/ui-automation-mobile).

Test automation is done on several levels represented by the test pyramid, but for the purposes of this article, we are concerned with UI test automation.

Read up on the test pyramid [here](https://martinfowler.com/articles/practical-test-pyramid.html).

![test-pyramid.png](/img/test-pyramid.png)

UI automation entails writing a test script which will perform the same actions a human tester would on a particular piece of finished/built software.

There are plenty of tools available, but generally there are two approaches:

- Using a test framework and implementing tests by coding them.
- Using a test recorder which will record and play your actions.

You can code and run your tests using just a text editor or an actual IDE which will help you organize your tests and test data, connect to bug tracking systems, etc.

## Tools

### Web frameworks - Selenium

[Selenium](https://www.selenium.dev/) is probably the most popular web automation framework built on top of WebDriver (as many others are). We use it for web UI automation.

Selenium IDE was developed for testers and developers to record their actions as they follow the workflow that they need test.

There are plenty of competing tools and frameworks out there. To name a few:

- [Cypress](https://www.cypress.io/)
- [WebdriverIO](https://webdriver.io/)
- [Puppeteer](https://github.com/puppeteer/puppeteer)
- [Playwright](https://github.com/microsoft/playwright)

### Mobile frameworks - Appium

Selenium's mobile analogue, used for automating hybrid and native mobile apps. We use it for mobile UI automation.

**Appium is an:**

- open-source
- cross-platform (Android, iOS, others)
- automation tool
- for testing hybrid and native apps
- on simulators (iOS) or emulators (Android)
- and real devices (iOS, Android).

**Philosophy**

- You shouldn’t have to recompile your app or modify it in any way in order to automate it.
- You shouldn’t be locked into a specific language or framework to write and run your tests.
- A mobile automation framework shouldn’t reinvent the wheel when it comes to automation APIs.
- A mobile automation framework should be open source, in spirit and practice as well as in name!

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

---

![ui-test-automation.gif](/img/ui-test-automation.gif)
