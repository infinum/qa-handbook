
On a small project, or while you are working alone, you can get away with naming inconsistency since you are familiar with your code. 
As the project grows, or more people join, the work and maintenance become difficult.

When following a naming convention:
* writing code is easier since you don’t have to ponder over element naming
* good naming makes the code easier to read and understand
* collaboration is easier when everyone follows the same style

Basic principles:
* use only English
* be mindful of grammar
* names should be meaningful and concise
* avoid slang and unclear abbreviations
* be consistent

Code examples are in Python and comply with [PEP 8 – Style Guide for Python Code](https://peps.python.org/pep-0008/#a-foolish-consistency-is-the-hobgoblin-of-little-minds).

When it comes to name casing, _snake_case_ (lower case with underscores separating the words) should be used as per Python naming convention.


## Variables

You should use _nouns_ or _short phrases with adjectives_ to describe what is stored in the variable

**Bad:**

`dwtz`

`User_with_name_and_age`

**Better:**

`date_with_timezone`

`user_data`


**Boolean**

When naming a variable that stores a boolean value, think of it as asking a question to which the answer is _Yes_ or _No_.

**Bad:**

`ok`

`correct`

**Better:**

`is_valid`

`is_correct`


**Constants**

Should be written in all capital letters with underscores separating words.
Constants should store values that never change.

**Bad:**

`name_of_the_app`

**Better:**

`APP_NAME`


## Methods / Functions

Functions and methods perform an action such as returning a value after a calculation, checking if a value is valid, etc.
Therefore, you typically want to use _verbs_ or _short phrases with adjectives_ that describe what the function or a method does.

When getting a value, always start the name with `get_` and use it consistently throughout the project. Do not switch between synonyms like _fetch_ or _retrieve_.

**Bad:**

`now()`

**Better:**

`get_current_time()`


When returning a `boolean` value it must be clear from the method name that it returns a boolean value and not some other type.

**Bad:**

`valid_email()`

`name_in()`

**Better:**

`is_email_valid()`

`has_name()`


Depending on whether you are writing a function that stands on its own, or a method which belongs to an object, you might want to consider the name length.
If a functions stands on its own, it would be better to write a clearer name, such as `save_user_data`.
If a method belongs to the `User` object, it could be named `save_data`.


## Classes

Use _nouns_ or _short phrases with nouns_ that describe the object the class creates.

When it comes to name casing, use _upper camel case_ for class names.

**Bad:**

`pagethathandleslogin`

`dialog_window`

**Better:**

`class LoginPage`

`class DialogWindow`


## Files

Apply the same rules as for the variables.

**NOTE:** Careful with short names such as `email` because in might clash with the existing `email` module and break your code.

**Bad:**

`email`

`settingsPage`

**Better:**

`email_methods`

`settings_page`


## Example

Tests are methods so consider the naming convention when writing the test name as well.
In most frameworks, a test method must have either the prefix `test_` or the suffix `_test`.
The rest is up to you. Following the basic principles, write meaningful and concise names without too much redundant information.

In case of a page class, you can add `__` before locator name to make it "_private_" and only available to the methods of the page class.


### Page class
     
    class CreateProjectPage(BasePage):
    
        def __init__(self, driver, environment, package_name, platform):
            super().__init__(driver, environment, package_name, platform)
    
            self.__create_project_button_locator = {
                ANDROID: (MobileBy.ID, f"{self.package_name}:id/btnSubmit"),
                IOS: (MobileBy.ACCESSIBILITY_ID, "Create")
            }
    
            self.__project_name_input_locator = {
                ANDROID: (MobileBy.ACCESSIBILITY_ID, "Project name"),
                IOS: (MobileBy.ACCESSIBILITY_ID, "Project name")
            }
    
        @property
        def create_project_button(self):
            return self.get_present_element(self.__create_project_button_locator[self.platform])
    
        @property
        def project_name_input(self):
            return self.get_present_element(self.__project_name_input_locator[self.platform])


### Test class 

    class TestProjectScenarios:
    
        def test_create_project(self, initialize_pages):

            project_name = "Project"            

            self.create_project_page.project_input_field.send_keys(project_name)
            self.create_project_page.create_project_button.click()

            check.is_equal(self.project_page.project_name.text, project_name)
