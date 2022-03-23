> *Where is the 'any' key? - Homer Simpson*


## What is CSS?
[CSS](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/What_is_CSS) stands for _Cascading Style Sheets_. It is a language used for styling HTML documents, i.e. it describes the layout of the HTML document, how elements should look like, and so on.


### CSS syntax

CSS is a rule-based language, meaning that the instructions look like a set of rules or data, as opposed to the languages like Python where the instructions form a list of steps in a sequence.
A CSS rule consists of a selector (one or more) and a declaration block enclosed by `{}` brackets.

Example showing how to style level one heading `h1` by specifying the text `color`, and the `font-family`.

`
h1 {
    color: red;
    font-family: Arial, Helvetica, sans-serif;
}
`

## What are CSS selectors?

A CSS selector is an arrangement of an element selector and value that locate the element on a web page. 
Using the example above, a CSS selector would be the `h1` element. 

`title_locator = driver.find_element_by_css_selector('h1')`


### Types of CSS selectors

There are quite a few selectors you can use to get the desired element, some of which are:

- ID
- Class
- Attribute
- Substring


#### ID

`id` in CSS is represented by `#`

HTML: 

`<input id="toggle-all" class="toggle-all" type="checkbox">`


Selenium CSS selector: 

`toggle_all_button = driver.find_element_by_css_selector('#toggle-all')`


#### Class

`class` in CSS is represented by `.`

HTML: 

`<input class="toggle" type="checkbox">`

Selenium CSS selector: 

`selected_button = driver.find_element_by_css_selector('.selected')`


#### Attribute

When using the attribute selector, there are a few options to play around with.
Using only the attribute as a locator probably won't result in a unique element since quite a few elements could be using the same attribute.

You can, however, combine the attribute with an _id_, _tag_, _class_ and so on. 
Furthermore, you can also specify the exact values to match, values that start with a specific string, values that contain a specific string, and so on.

HTML: 

`<a href="http://todomvc.com">TodoMVC</a>`

Attribute only: 

`[type="checkbox"]`

Id and attribute: 

`.toggle[type="checkbox"]`

Tag and attribute: 

`a[href="http://todomvc.com"]`

Selenium CSS selector: 

`checkbox_button = driver.find_element_by_css_selector('a[href="http://todomvc.com"]')`


Check [Attribute selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors) for more examples.

#### Substring

When working with strings you can use various mechanisms to match a substring.
Use the appropriate symbol for the corresponding matching mechanism.

Prefix match
- matches the href attribute that starts with text "_http:_": 

`[href^="http:"]`

Suffix match
- matches the href attribute that ends with text "_.com_": 

`[href$=".com"]`

Sub-string match
- matches the href attribute that contains text "_todomvc_": 

`[href*="todomvc"]`

Selenium CSS selector:

`checkbox_button = driver.find_element_by_css_selector('[href^="http://todo"]')`

### Navigating through elements

Using a specific syntax you can specify how to navigate to an element.
For example, using the `>` symbol between two elements refers to direct descendants, while the `,` refers to all elements.

Select `a` that are child of `li`: 

`li a`

Select direct `a` descendants of `li`: 

`li > a`

Select all `a` and `li` elements: 

`li, a`

Select `a` element following a `li` element: 

`li ~ a`

#### Pseudo selectors

In CSS, _pseudo-class_ is a keyword added to an element to define its state. For example, the color of a button can change on hover or when active. 
Pseudo-classes start with a colon `:`

Select an element that is being clicked: 

`:active`

Select a link that has already been clicked: 

`:visited`

Select the first element inside another element (the first _child_): 

`:first-child`

Select the last element inside another element (the last _child_): 

`:last-child`

Select the _nth_ element inside another element. The passed parameter can be: an integer, _even_, _odd_, or a formula 

`:nth-child(parameter)` 


### Combining multiple selectors

You can also combine multiple selectors to further narrow your search for an element.
There are multiple ways to do it, below are just some examples.

Tag and an attribute that starts with a specified text: 

`a[href^="http://todo"]`

Combining tag navigation with an attribute that ends with specified text: 

`p > a[href*="todomvc.com"]`


## How to use Chrome DevTools to find a CSS selector

Writing CSS is sometimes tricky. It is useful to know your way around DevTools to help you with finding the right selector. 
[TodoMVC](https://todomvc.com/examples/vanillajs/) app was used as an example.

1. Press **Fn + F12** to open _DevTools_

2. Open _Elements_ tab

3. While the Elements tab is active, press **Cmd + F** to open the search field

4. Type in a CSS selector 
 - If there is a match, the element(s) will be highlighted in the DOM
 
Select the _All_ button: 

`.selected`

<span style="display:block; border: 1px solid #e0e0e0;">![selenium_locators_CSS_devtools_1.png](/img/selenium_locators_css_devtools_1.png)</span>

Select the _second_ todo element: 

`ul > li:nth-child(2) input`

<span style="display:block; border: 1px solid #e0e0e0;">![selenium_locators_CSS_devtools_2.png](/img/selenium_locators_css_devtools_2.png)</span>



## Additional resources

For more information and examples take a look at the following resources:

[MDN CSS selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors)

[CSS selectors cheatsheet](https://dev.to/dawnind/css3-selectors-cheat-sheet-6dk)

Web game to help you learn how to use CSS selectors:

[CSS Diner](https://flukeout.github.io/)

---


![dilbert_selenium_css.png](/img/dilbert_selenium_css.png)

*Image downloaded from [dilbert.com](https://dilbert.com/strip/2021-09-03): 09-03-21 by Scott Adams*
