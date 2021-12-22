> The bitterness of poor quality remains long after the sweetness of low price is forgotten. - Benjamin Franklin


## What are WebElements?

A **WebElement** is an element such as a button, checkbox, input field, or any kind of element present on the webpage.

To interact with a WebElement, you first need to locate that element on the page. Selenium WebDriver API offers, among other functionalities, built-in methods for finding WebElements using various properties/locators: *ID*, *XPath*, *CSS selector*, *Name*, *Class name*, *Tag name*, *Link text*, and *Partial link text*.

## Which locator to use?

You want to use a unique locator for every element. Most of the time that will be the **ID** of an element.
In case the ID is not present, try Name, XPath, or CSS selector. Anyway, make sure that the locator is unique and that you are getting the correct one.

## Locator strategies
Based on the available locators, the following methods are available:

Methods that return a **single** element, the first one found:

 - `find_element_by_id`
 - `find_element_by_name`
 - `find_element_by_xpath`
 - `find_element_by_link_text`
 - `find_element_by_partial_link_text`
 - `find_element_by_tag_name`
 - `find_element_by_class_name`
 - `find_element_by_css_selector`

Methods that return all (a **list** of) elements matching the property:

 - `find_elements_by_name`
 - `find_elements_by_xpath`
 - `find_elements_by_link_text`
 - `find_elements_by_partial_link_text`
 - `find_elements_by_tag_name`
 - `find_elements_by_class_name`
 - `find_elements_by_css_selector`
 

### NoSuchElementException
More often than not, you will come across `NoSuchElementException`. 
The exception tells you that you are trying to get an element that does not exist on the page. The element might really be missing, maybe you are using the wrong locator to get it, or maybe you simply have a typo in your code.

Take another look at your code, there could be simply a character missing :)


## Additional resources

For more info read the [locating elements chapter](https://selenium-python.readthedocs.io/locating-elements.html) in the _Selenium with Python_ document.

---


![dilbert_selenium_strategies.png](/img/dilbert_selenium_strategies.png)
