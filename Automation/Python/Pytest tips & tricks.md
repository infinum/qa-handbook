## What is pytest?

Pytest is a testing framework for Python. For more info, check the [documentation](https://pytest.org).


### Conftest

`conftest.py` is a file in which you can set up your test configuration. The file should primarily consist of fixtures which are automatically detected and executed.


You can have multiple `conftest` files in your project. For example, you can have one `conftest` in the project root where you want to set up logic for the entire project. This one might be useful for the overall configuration, like setting up driver(s). And then you can also add an additional `conftest` file into your tests directory. In `tests/conftest.py` you could have fixtures that are used only on tests. Note that all tests will use those fixtures.


You can even add another `conftest` in other test subdirectories. For example, directory `test_a` could have its own conftest `tests/test_a/conftest.py`.


The structure might look something like this:

```
ROOT
conftest.py
└── tests
    └── conftest.py
    └── test_a
        └── conftest.py
        └── test_file_a.py
    └── test_b
        └── test_file_b.py
```


### Autouse

Let's say there is some code that you want to run before or after every test, but you do not want to call it every time. `autouse` option comes in handy. By setting the `autouse` parameter in a fixture to `True`, it is called automatically.


```python
import pytest

@pytest.fixture(scope="function", autouse=True)
def fixture_a():
    """Executed automatically before every test."""
    # Some code


@pytest.fixture(scope="class", autouse=True)
def fixture_b(driver):
    """Executed automatically after every class."""
    yield driver
    # Some code
```

Check the docs on [autouse](https://docs.pytest.org/fixture.html#autouse-fixtures-fixtures-you-don-t-have-to-request) for more details.


### Fixtures and Hooks

Fixtures are defined using the `@pytest.fixture` decorator. They ensure the setup and teardown of resources before and after tests, providing a clean and consistent testing environment. 
Hooks are used for customizing the behavior of the testing framework itself and they are triggered at specific points during the test execution process. 

Few things to have in mind when working with Fixtures and Hooks:

- Fixtures are created when first requested by a test, and are destroyed based on their scope. Possible values for scope are `function` (default), `class`, `module`, `package` or `session`.
- Hooks do not have scope.
- Hook functions can be grouped into plugins. 
- You can use hooks to customize test reporting.
- Fixtures cannot be called from a Hook function.


### Soft asserts

If you need soft asserts in your tests, [pytest-check](https://pypi.org/project/pytest-check/) is a very useful plugin for pytest. It is easy to use and understand.

Example:

```python
# test_file.py
import pytest_check as check

def test_example():
    check.is_true(1 > 2)

    check.equal("abc", "def")
```


### Importing custom plugins

On occasion you will have to, or want to, create a custom plugin. Or just extract some of the code from `conftest`. For pytest to discover the plugin, it has to be somehow specified in a `conftest` file.

For example, you decided to add custom `html_report` and `slack` plugins. One way to do it is like this:

```python
# conftest.py
pytest_plugins = [
    "utilities.plugins.html_report.plugin",
    "utilities.plugins.slack.plugin",
]
```
