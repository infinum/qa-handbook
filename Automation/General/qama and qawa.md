> All code is guilty, until proven innocent.

`qama` and `qawa` are our **template projects** for test automation.

The idea behind them is to help you quickly start writing maintainable and easy to understand UI tests.
While **qama** is designed to work primarily with mobile, **qawa** focuses on web projects.


## Project structure

Both projects are structured using the _page object model_.

In short, that means that:

- Locators are placed in a page class.
- Tests are placed in a test class.

More on page object model:
- [Martin Fowler - PageObject](https://martinfowler.com/bliki/PageObject.html)
- [Selenium docs - Page object Models](https://www.selenium.dev/documentation/test_practices/encouraged/page_object_models)


## qama

`qama` stands for `QA Mobile Automation.`
It also happens to be a [sword](https://en.wikipedia.org/wiki/Qama). :)

It is based on the [pytest framework](https://docs.pytest.org) and [Appium](https://appium.io).
See [README](https://github.com/infinum/qama#readme) for more details and setup instructions.


## qawa

`qawa` stands for `QA Web Automation.`

It is based on the [pytest framework](https://docs.pytest.org) and [Selenium](https://www.selenium.dev).
See [README](https://github.com/infinum/qawa#readme) for more details and setup instructions.
