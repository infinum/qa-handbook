## Web frameworks

[Playwright](https://playwright.dev/) is a modern web automation framework that is becoming increasingly popular. It supports multiple browsers (Chromium, Firefox, WebKit), runs in headed or headless mode, and lets you write tests in JavaScript/TypeScript, Python, C#, or Java.

**Benefits of Playwright**

- Built-in auto-waiting, parallel execution, and strong isolation between tests
- Clear errors, debugging tools, and trace viewer
- Automatic waiting for elements and network conditions

**Other options**

[Selenium](https://www.selenium.dev/) remains a widely used framework built on WebDriver. It has a long-standing ecosystem, broad language support, and a large community. Selenium follows the W3C WebDriver standard, so it integrates well with many CI/CD and cloud testing providers. It’s a solid choice for existing projects or when you need WebDriver compatibility.

Other tools in this space include:

- [Cypress](https://www.cypress.io/)
- [WebdriverIO](https://webdriver.io/)
- [Puppeteer](https://github.com/puppeteer/puppeteer)

## Mobile frameworks - Appium

[Appium](https://appium.io/) extends Selenium’s WebDriver model to mobile: it automates hybrid and native apps on Android and iOS.

**Appium is:**

- Open-source and cross-platform (Android, iOS, and others)
- For testing hybrid and native apps on simulators (iOS), emulators (Android), or real devices

**Philosophy**

- You shouldn't have to recompile your app or modify it in any way to automate it
- You shouldn't be locked into a specific language or framework to write and run your tests
- It shouldn't reinvent the wheel when it comes to automation APIs
- It should be open source in spirit and practice

**How does it do it?**

- Uses the WebDriver API and wraps vendor-provided frameworks (XCUITest on iOS, UiAutomator on Android)
- Speaks a REST client-server protocol (e.g. W3C WebDriver); the server is written in Node.js

**Advantages**

- Write tests in WebDriver-compatible languages with Appium extensions
- Use any testing or execution framework; Appium is an automation library, not a framework
- Includes an inspector for viewing UI elements

## Testing API

A great tool to start with API testing is Postman. You can easily pick up the basics and start testing the API right away.
Postman can be used in manual testing, but also offers a few options for automation.

For more info read the [Using Postman](https://infinum.com/handbook/qa/tools/using-postman) article.

**What to test**

When it comes to API there are quite a few details that need checking.
Unfortunately, oftentimes only the status code is being checked. However, especially nowadays with apps doing wonders, that won't cut it.

A few basic things to check:

- status codes (all that apply, not only 200)
- response payload
- response headers

Read the [REST API Testing Strategy](https://www.sisense.com/blog/rest-api-testing-strategy-what-exactly-should-you-test/) article for more ideas on what to check.
