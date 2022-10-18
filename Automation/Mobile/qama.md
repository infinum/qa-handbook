> All code is guilty, until proven innocent.

## qama

`qama` stands for `QA Mobile Automation.`
It also happens to be a [sword](https://en.wikipedia.org/wiki/Qama). :)

`qama` is a _template project_ with which you can quickly start writing maintainable UI tests for your mobile projects. It is based on the [pytest framework](https://docs.pytest.org/en/7.1.x/index.html) and [Appium](https://appium.io/). For more details see the [qama README](https://github.com/infinum/qama/blob/master/README.md).

It is very similar to `qawa` which was described [in this handbook article](https://infinum.com/handbook/qa/automation/web/selenium-and-qawa).

### Setup

Before you start using `qama`, there are a few things you need to set up.
Check the [Appium setup](https://infinum.com/handbook/qa/automation/mobile/appium-setup) article for further instructions.


## Project structure

`qama` is structured using _page object model_.

In short, that means that:

- locators are placed in the appropriate page class.
- tests are placed in the appropriate test class

To learn more, read [this page object model](https://martinfowler.com/bliki/PageObject.html) article.


## Page class example

- Every page class has to inherit properties and methods from the `BasePage` class
- Every locator has to be a dictionary to support multiple platforms (currently Android and iOS)
- Every property has to be decorated with the `@property` decorator


```python
from appium.webdriver.common.appiumby import AppiumBy

import conftest
from base_page import BasePage


class HomePage(BasePage):

    def __init__(self, driver, environment, platform):
        super().__init__(driver, environment, platform)

        self.__project_name_input_locator = {
            conftest.ANDROID: (AppiumBy.ACCESSIBILITY_ID, "project_name_edit_text"),
            conftest.IOS: (AppiumBy.ACCESSIBILITY_ID, "enter_project_name_textfield")
        }

        self.__create_project_button_locator = {
            conftest.ANDROID: (AppiumBy.ID, "createProjectButton"),
            conftest.IOS: (AppiumBy.ACCESSIBILITY_ID, "create_project_button")
        }

    @property
    def project_name_input(self):
        return self.get_present_element(self.__project_name_input_locator[self.platform])

    @property
    def create_project_button(self):
        return self.get_present_element(self.__create_project_button_locator[self.platform])
```

## Test class example

- Pages used in tests are initialized in the `initialize_pages` fixture which is called before each test
- Every test file has to be prefixed with `test_` (as in `test_welcome.py`)
- Every test class has to be prefixed with `Test` (as in `TestHome`)
- Every test method has to be prefixed with `test_` (as in `test_onboarding`)


```python
from logging import info

import pytest
import pytest_check as check

from pages.home_page.home_page import HomePage


class TestHome:

    @pytest.fixture(scope="function", autouse=True)
    def set_up(self, driver, environment, platform):
        self.home_page = HomePage(driver, environment, platform)

    @pytest.mark.smoke
    def test_onboarding(self, extra):
        self.home_page.select_language_english()
        self.home_page.next_button.click()

        self.home_page.terms_of_use_checkbox.click()
        self.home_page.privacy_notice_agree_button.click()

        check.is_true(self.home_page.create_project_button.is_enabled())
        self.home_page.save_screenshot(extra)
```

### Asserts

The idea of a test is to verify some result. Therefore, each test must contain at least one assert.

For more info on assertions, read:

- [Writing assertions](https://beta.infinum.com/handbook/qa/automation/web/selenium-and-qawa#writing-assertions)
- [Asserts](https://infinum.com/handbook/qa/automation/general/way-of-working#asserts)


## Appium server logs

Server logs can be helpful when debugging Appium issues. Due to potential security issues, the option is disabled by default. 
If you want to have server logs available during test runs, start Appium server by running: 

```
appium --allow-insecure=get_server_logs
```

**NOTE**:

- Use the `--allow-insecure` option only if you are running the server in a secure environment.

Read [Appium Security](https://appium.io/docs/en/writing-running-appium/security/index.html#insecure-features) for more information.


### Enable saving server logs in QAMA

The method for saving the logs is already implemented in `QAMA`.

There are a few more steps to take to finish the implementation. 

- Add `logs` folder to the project root
    - This folder will store the generated logs


- Call the `__save_logs` method in the `driver` fixture in the `conftest.py`

```python
yield driver

__save_logs(driver, f"{ROOT_DIR}/logs/appium_server_{system_port}_{device_udid}.log", "server")

driver.quit()
```

- Update the `start_appium_server.sh` script in `utilities/scripts` to use the following command:

```sh
osascript -e 'tell app "Terminal" to do script "appium --allow-insecure=get_server_logs"'
```
