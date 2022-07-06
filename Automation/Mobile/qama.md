> *All code is guilty, until proven innocent.*

## qama

`qama` stands for `QA Mobile Automation.`
It also happens to be a [sword](https://en.wikipedia.org/wiki/Qama). :)

- It is a **template project** that will help you quickly start writing maintainable UI tests for your mobile projects.
- See the [qama README](https://github.com/infinum/qama/blob/master/README.md) for details. It uses Python + Appium.
- It is very similar to `qawa` which was described in [in this handbook article](https://infinum.com/handbook/qa/automation/web/selenium-and-qawa). 


## Example of a page class

Other than the boring config files, the difference between our web & mobile boilerplate code is mostly reflected in the page classes where every locator is a dictionary that contains both Android & iOS entries.

	
	from utilities.base_page import BasePage
	from utilities import config
	from appium.webdriver.common.mobileby import MobileBy
	
	
	class HomePage(BasePage):

    login_button_locator = {
        "android": (MobileBy.ID, config.package_name + ":id/loginButton"),
        "ios": (MobileBy.ACCESSIBILITY_ID, "login_button"),
    }

    pin_input_field_locator = {
        "android": (MobileBy.ID, config.package_name + ":id/pin"),
        "ios": (MobileBy.ACCESSIBILITY_ID, "pin_input_field"),
    }

    @property
    def login_button(self):
        return self.get_present_element(self.login_button_locator[config.platform])

    @property
    def pin_input_field(self):
        return self.get_present_element(self.pin_input_field_locator[config.platform])

---

![dil-code.jpg](/img/dil-code.jpg)

