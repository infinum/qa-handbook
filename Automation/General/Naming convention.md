> Talent wins games, but teamwork and intelligence win championships. – Michael Jordan

## Why follow a naming convention:

- writing code is easier since you don’t have to ponder over element naming

- good naming makes the code easier to read and understand

- collaboration is easier when everyone follows the same style

On a small project, or while working alone, you might get away with naming inconsistency.
As the project grows, or more people join, the code becomes less readable and the work and maintenance more difficult.

## Basic principles:

- use only English

- be mindful of grammar

- names should be meaningful and concise

- avoid slang and unclear abbreviations

- be consistent

When it comes to name casing, you should use _snake_case_ (lower case with underscores separating the words) as per Python naming convention.

Code examples mentioned here are in Python and comply with [PEP 8 – Style Guide for Python Code](https://peps.python.org/pep-0008/#a-foolish-consistency-is-the-hobgoblin-of-little-minds).

## Variables

You should use _nouns_ or _short phrases with adjectives_ to describe what is stored in the variable.

**Bad:**

`dwtz`

`User_with_name_and_age`

**Better:**

`date_with_timezone`

`user_data`

### Boolean

When naming a variable that stores a boolean value, think of it as asking a question to which the answer is _Yes_ or _No_.

**Bad:**

`ok`

`correct`

**Better:**

`is_valid`

`is_correct`

### Constants

For constants, use all capital letters with underscores separating words.
Constants should store values that never change.

**Bad:**

`name_of_the_app`

**Better:**

`APP_NAME`

## Methods / Functions

Functions and methods perform an action such as returning a value after a calculation, checking if a value is valid, etc.
You typically want to use _verbs_ or _short phrases with adjectives_ that describe what the function or method does.

**Bad:**

`name()`

**Better:**

`get_name()`

### Boolean

When a function returns a `boolean` value, it must be clear from the name that the return type is a boolean value.

**Bad:**

`valid_email()`

`name_in()`

**Better:**

`is_email_valid()`

`has_name()`

Depending on whether you are writing a function that stands on its own, or a method which belongs to an object, you might want to consider the name length.
If a function stands on its own, it would be better to write a clearer name, such as `save_user_data`.
If a method belongs to the `User` object, you could name it `save_data`.

## Classes

Use _nouns_ or _short phrases with nouns_ that describe the object the class creates.

When it comes to name casing, use _upper camel case_ for class names.

**Bad:**

`pagethathandleslogin`

`dialog_window`

**Better:**

`LoginPage`

`DialogWindow`

## Packages and modules

Packages and modules should have short, all-lowercase names.
The use of underscores is discouraged, however, you can add them to improve readability or to avoid name collision.

**NOTE:** Be careful with short names such as `email` because it might collide with the existing `email` module and break your code. In this case, you could use `email_methods` or similar instead.

**Bad:**

`emailmodule`

`helperMethods`

**Better:**

`email_module`

`helper_methods`

## Example: UI elements and methods

The tables below show a few examples on how to use suffixes and prefixes in your project to make the code easy to understand.
Use them consistently.

### Variables

| UI     | Suffix   | Example            |
| :----- | :------- | :----------------- |
| Button | \_button | submit_button      |
| Image  | \_image  | profile_image      |
| Label  | \_label  | project_name_label |
| Slider | \_slider | volume_slider      |

### Methods / Functions

| Action            | Prefix     | Example                |
| :---------------- | :--------- | :--------------------- |
| Get current time  | get\_      | get_current_time()     |
| Generate a name   | generate\_ | generate_random_name() |
| Clear name field  | clear\_    | clear_name_field()     |
| Open user details | open\_     | open_user_details()    |

## Example: page and test classes

Tests are functions so consider the naming convention when writing the test name.
In many frameworks, a test function must have either the prefix `test_` or the suffix `_test`.
The rest is up to you. Following the basic principles, write meaningful and concise names without redundant information.

In case of a page class, you can add `__` before the locator name to make it "_private_" and only available to the methods of the page class.

### Page class

```
class ProjectPage(BasePage):

    def __init__(self, driver, environment, platform):
        super().__init__(driver, environment, platform)

        self.__create_project_button_locator = {
            ANDROID: (MobileBy.ID, "btnSubmit"),
            IOS: (MobileBy.ID, "Create")
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
```

### Test class

```
class TestProject:

    def test_create_project(self):
        self.project_page.project_name_input.send_keys(project_name)
        check.is_true(self.project_page.create_project_button.is_enabled())
```
