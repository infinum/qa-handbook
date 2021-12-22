> *Debugging is twice as hard as writing the code in the first place. Therefore, if you write the code as cleverly as possible, you are, by definition, not smart enough to debug it.*

## qawa

`qawa` stands for `QA Web Automation.`

- It is our **template project** that will help you quickly start writing maintainable UI tests for your web projects.
- See the [qawa README](https://github.com/infinum/qawa/blob/master/README.md) for details. It uses Python + Selenium.

## Page object model

`qawa` uses POM (page object model), also called the page object pattern.

Read up on it [here](https://martinfowler.com/bliki/PageObject.html).

## Example of a page class

	from utilities.base_page import BasePage
	from selenium.webdriver.common.by import By

	class BlogPage(BasePage):

    slug = "/the-capsized-eight"
    shameless_link_locator = (By.LINK_TEXT, "Shameless")
    topic_label_locator = (By.CLASS_NAME, "__highlight")

    def navigate_to_page(self):
        self.navigate(self.slug)

    @property
    def shameless_link(self):
        return self.get_present_element(self.shameless_link_locator)

    @property
    def topic_label(self):
        return self.get_present_element(self.topic_label_locator)
        
- Each page class inherits from BasePage.
- Each page class can contain a slug, locators, properties, and helper methods.

## Example of a test class
	from utilities.base_test import BaseTest
	from utilities.loggers import log_message
	from pages.blog_page import BlogPage


	class BlogTests(BaseTest):
	    def setUp(self):
	        super().setUp()
	        self.blog_page = BlogPage(self.driver)

    def test_navigate_to_shameless_posts(self):
        log_message(
            "Navigates to Shameless blog posts and verifies that the topic label is Shameless."
        )

        self.blog_page.navigate_to_page()
        self.blog_page.shameless_link.click()
        self.blog_page.save_screenshot("shameless")

        self.assertTrue(self.blog_page.topic_label.text == "Shameless")
        
- Each test class inherits from BaseTest.
- Each test class initializes the Pages it will use by overriding setUp.
- Each test method has to begin with `test_`.
- Each test method should contain at least one assertion.

## Writing assertions

Some common assertion methods in unittest.

Checking that something exists:

	self.assertTrue(self.page.button)
	
Checking that something does not exist:

	self.assertFalse(self.page.button)
	
Checking that something is equal:

	self.assertEqual(self.page.button.text, "Logout")
	
Checking that something is not equal:

	self.assertNotEqual(self.page.button.text, "Logout")


## Additional resources

- [Cypress.io best practices](https://docs.cypress.io/guides/references/best-practices.html) (applicable to web UI automation in general)
- [Arrange Act Assert](http://wiki.c2.com/?ArrangeActAssert)

---

![dil-ai.png](/img/dil-ai.png)
