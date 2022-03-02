> *“It’s automation, not automagic.” - Jim Hazen*


## What is CSS?
[CSS](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/What_is_CSS) stands for _Cascading Style Sheets_. It is a language used for styling HTML documents, i.e. it describes the layout of the HTML document, how elements should look like, and so on.


### CSS syntax

CSS is a rule-based language, meaning that the instructions look like a set of rules or data, as opposed to the languages like Python where the instructions form a list of steps in a sequence.
A CSS rule consists of a selector (one or more) and a declaration block enclosed by `{}` brackets

Example showing how to style level one heading `h1` by specifying the text `color`, and the `font-family`.

`
h1 {
    color: red;
    font-family: Arial, Helvetica, sans-serif;
}
`

## What are CSS selectors?

A CSS selector is an arrangement of an element selector(s) and value(s) that locate the element on a web page. 
Using the example above, a CSS selector would be the `h1` element. 

`title_locator = driver.find_element_by_css_selector('h1')`


### Types of CSS selectors

There are quite a few selectors you can use to get the desired element, some of which are:

- ID
- Class
- Attribute
- Sub-string
- Inner string


#### ID

`#toggle-all`

`toggle_all_button = driver.find_element_by_css_selector('#toggle-all')`

#### Class

`.selected`

`selected_button = driver.find_element_by_css_selector('.selected')`

#### Attribute



`.toggle[type="checkbox"]`

`a[href="http://todomvc.com"]`

`checkbox_button = driver.find_element_by_css_selector('a[href="http://todomvc.com"]')`

When using the attribute selector, there are quite a few options to play around with.
You can look for, among others, the exact values, like in the example above, values that start with a specific string, values that contain a specific string, and so on.

Check [Attribute selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors) for more examples.

#### Sub-string


#### Inner string


###


## How to use Chrome DevTools to find CSS selector

Writing CSS is sometimes tricky. It is useful to know your way around DevTools to help you with finding the right selector. 
[TodoMVC](https://todomvc.com/examples/vanillajs/) app was used as an example.

1. Press **Fn + F12** to open _DevTools_

2. Open _Elements_ tab

3. While the Elements tab is active, press **Cmd + F** to open the search field

4. Type in a CSS selector 
 - If there is a match, the element(s) will be highlighted in the DOM
 
Select the _All_ button:

`.selected`

![selenium_locators_CSS_devtools_1.png](/img/selenium_locators_css_devtools_1.png)

Select the _second_ todo element:

`ul > li:nth-child(2) input`

![selenium_locators_CSS_devtools_2.png](/img/selenium_locators_css_devtools_2.png)



## Additional resources

For more information and examples take a look at the following resources:

[MDN CSS selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors)

[CSS selectors cheatsheet](https://dev.to/dawnind/css3-selectors-cheat-sheet-6dk)

---


![dilbert_selenium_css.png](/img/dilbert_selenium_css.png)