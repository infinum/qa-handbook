> *All code is guilty, until proven innocent.*

## qama

`qama` stands for `QA Mobile Automation.`
It also happens to be a [sword](https://en.wikipedia.org/wiki/Qama). :)

`qama` is a _template project_ with which you can quickly start writing maintainable UI tests for your mobile projects.
It is based on the [pytest framework](https://docs.pytest.org/en/7.1.x/index.html) and [Appium](https://appium.io/). 
For more details see the [qama README](https://github.com/infinum/qama/blob/master/README.md).

It is very similar to `qawa` which was described [in this handbook article](https://infinum.com/handbook/qa/automation/web/selenium-and-qawa).

### Setup

Before you start using `qama`, there are a few things you need to set up.
Check the [Appium setup](https://infinum.com/handbook/qa/automation/mobile/appium-setup) article for further instructions.


## Project structure

`qama` is structured using [page object model](https://martinfowler.com/bliki/PageObject.html).


## Example of a page class

The main difference between `qama` and `qawa` is mostly reflected in the page classes. 
To adjust the code for multiple platforms, every locator is a dictionary that contains locators for both Android and iOS.
During runtime, the appropriate locator is passed to the test that uses it.


    import conftest
    from base_page import BasePage
    from appium.webdriver.common.mobileby import MobileBy

    
    class HomePage(BasePage):

    def __init__(self, driver, environment, package_name, platform):
        super().__init__(driver, environment, package_name, platform)

        self.__project_name_input_locator = {
            conftest.ANDROID: (MobileBy.ACCESSIBILITY_ID, "project_name_edit_text"),
            conftest.IOS: (MobileBy.ACCESSIBILITY_ID, "enter_project_name_textfield")
        }

        self.__create_project_button_locator = {
            conftest.ANDROID: (MobileBy.ID, f"{self.package_name}:id/createProjectButton"),
            conftest.IOS: (MobileBy.ACCESSIBILITY_ID, "create_project_button")
        }

    @property
    def project_name_input(self):
        return self.get_present_element(self.__project_name_input_locator[self.platform])

    @property
    def create_project_button(self):
        return self.get_present_element(self.__create_project_button_locator[self.platform])


## Example of a page class

    
    import pytest
    from logging import info
    from pages.home_page.home_page import HomePage
    
    
    class TestHome:

    @pytest.fixture(scope="function", autouse=True)
    def initialize_pages(self, driver, environment, package_name, platform):
        self.home_page = HomePage(driver, environment, package_name, platform)

    @pytest.mark.smoke
    def test_onboarding(self, extra):

        self.home_page.select_language_english()

        self.home_page.next_button.click()

        self.home_page.terms_of_use_checkbox.click()
        self.home_page.privacy_notice_agree_button.click()

        assert self.home_page.create_project_button.is_enabled(), f"Button should be enabled."

        self.home_page.save_screenshot(extra)
