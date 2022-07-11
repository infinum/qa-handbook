> *Debugging is twice as hard as writing the code in the first place. Therefore, if you write the code as cleverly as possible, you are, by definition, not smart enough to debug it.*

## qawa

`qawa` stands for `QA Web Automation.`

- It is our **template project** that will help you quickly start writing maintainable UI tests for your web projects.
- See the [qawa README](https://github.com/infinum/qawa/blob/master/README.md) for details. It uses Selenium and Python in combination with the `pytest` framework.

## Page object model

`qawa` uses POM (page object model), also called the page object pattern.

Read up on it [here](https://martinfowler.com/bliki/PageObject.html).

## Installing Selenium and webdrivers

1. Install Homebrew (and Python 3 if it is not installed)
2. Install Selenium: `pip3 install selenium`
3. Install ChromeDriver (for Chrome): `brew install chromedriver`
4. Install geckodriver (for Firefox): `brew install geckodriver`


## Example of a page class

- Each page class inherits from BasePage.
- Each page class can contain a slug, locators, properties, and helper methods.


    from base_page import BasePage
    from selenium.webdriver.common.by import By


    class BlogPage(BasePage):

    slug = "/blog"
    blog_name_label_locator = (By.CLASS_NAME, "blog-intro__heading")

    def navigate_to_page(self):
        self.navigate(self.slug)

    @property
    def blog_name_label(self):
        return self.get_present_element(self.blog_name_label_locator)

    def wait_for_blog_page_to_load(self):
        self.wait_until_element_visible(self.blog_name_label_locator)

## Example of a test class

- Each test class initializes the pages it will use by using the `set_up` fixture.
- Each test class has to begin with `Test` (example: TestBlog).
- Each test `.py` file needs to be prefixed with `test_` (`test_*.py`).
- Each test method has to begin with `test_`.
- Each test method should contain at least one assertion.


    import pytest
    from logging import info
    from pages.blog_page import BlogPage
    from pages.home_page import HomePage
    import pytest_check as check


    class TestBlog:

    @pytest.fixture(scope="function")
    def set_up(self, driver, environment):
        self.blog_page = BlogPage(driver, environment)
        self.home_page = HomePage(driver, environment)

        self.home_page.navigate_to_page()

    def test_navigate_to_blog_page(self, set_up, extra):
        info("Navigates to blog posts and verifies that the blog title is correct.")

        self.home_page.blog_navigation_button.click()
        self.blog_page.wait_for_blog_page_to_load()
        self.blog_page.save_screenshot(extra)

        check.is_true(self.blog_page.blog_name_label.text == "Typing as we speak")

## Writing assertions

You can use either Python's standard `assert` (hard assert) or soft asserts using the [pytest_check](https://pypi.org/project/pytest_check/) plugin. You can read more about hard and soft asserts in [this handbook article](https://infinum.com/handbook/qa/automation/general/way-of-working#asserts).

### Python's standard assert examples

Checking that the button exists:

	assert self.page.button == True

Checking that the button text equals the expected value:

	assert self.page.button.text == "Logout"

### Soft assert examples

Here are some examples of assertion methods from the [pytest_check](https://pypi.org/project/pytest_check/) plugin. The plugin has to be imported into the test modules in order to be used. 

Checking that the button exists:

	pytest_check.is_true(self.page.button)

Checking that the button does not exist:

	pytest_check.is_false(self.page.button)
	
Checking that the button text equals the expected value:

	pytest_check.equal(self.page.button.text, "Logout")
	
Checking that the button text does not equal the expected value:

	pytest_check.not_equal(self.page.button.text, "Logout")


## Additional resources

- [Cypress.io best practices](https://docs.cypress.io/guides/references/best-practices.html) (applicable to web UI automation in general)
- [Arrange Act Assert](http://wiki.c2.com/?ArrangeActAssert)
- [pytest documentation](https://docs.pytest.org/)
