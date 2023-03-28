## What is Playwright?

Playwright is a test automation tool for Web testing. It supports testing on various browsers in both headed and headless mode. 
You can write tests in JavaScript / TypeScript, C#, Java and Python. Depending on your language of choice, the setup slightly differs.

This is a short and simple guide to quickly get started with Playwright for Python.


## Requirements

* Python 3.7 or newer.
* Check [Playwright troubleshooting](https://playwright.dev/python/docs/troubleshooting) for more details.


## Setup

1. Create a new PyCharm project 
   * Create and activate a [virtual environment](https://infinum.com/handbook/qa/automation/python/virtual-environment)
2. Install [pytest-playwright](https://pypi.org/project/pytest-playwright) plugin 
   * `pip install pytest-playwright`
3. Install browsers 
   * `playwright install`
4. Create a test file within the current working directory or a sub-directory
   * File name e.g.: `test_homepage.py`
   * See example test below
5. Run the test
   * On default (headless) browser:
     * `python3 -m pytest test_homepage.py`
   * On specific (headed) browser:
     * `python3 -m pytest test_homepage.py --browser firefox --headed`


## Example

```python
import re

from playwright.sync_api import Page, expect


def test_homepage(page: Page):
   page.goto("https://infinum.com/")

   # Expect a title "to contain" a substring
   expect(page).to_have_title(re.compile("Infinum"))

   # Create a locator for button
   accept_all_button = page.get_by_role("button", name="Accept all")

   # Take a screenshot
   page.screenshot(path="screenshot.png")

   # Click the button
   accept_all_button.click()

   # Expect the button to be hidden
   expect(accept_all_button).to_be_hidden()

   # Take a full page screenshot (screenshot of a full scrollable page)
   page.screenshot(path="screenshot_full_page.png", full_page=True)
```

### Resources

* [Infinum QA handbook - Virtual environment](https://infinum.com/handbook/qa/automation/python/virtual-environment)
* [Playwright for Python](https://playwright.dev/python/docs/intro)
* [Playwright GitHub](https://github.com/microsoft/playwright)
* [pytest-playwright plugin](https://pypi.org/project/pytest-playwright)
* [pytest](https://docs.pytest.org/en/7.2.x/) 
