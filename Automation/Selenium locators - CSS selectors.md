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

A CSS selector is an arrangement of elements that specify to which HTML element should the rules in the declaration block be applied. 
Using the example above, a CSS selector would be the `h1` element. 

The CSS selector syntax can also be used for locating elements on a web page.

`title_locator = driver.find_element_by_css_selector('h1')`


## How to use Chrome DevTools to find CSS selector

TODO - Update example and images

Writing CSS is sometimes tricky. It is useful to know your way around DevTools to help you with finding the right selector. 
[TodoMVC](https://todomvc.com/examples/vanillajs/) app was used as an example.

1. Press **Fn + F12** to open _DevTools_

2. Open _Elements_ tab

3. While the Elements tab is active, press **Cmd + F** to open the search field

4. Type in a CSS selector 
 - If there is a match, the element(s) will be highlighted in the DOM

Examples from the images below

Select the _All_ button:

`.selected`

Select the _second_ todo element:

`//*[@class="todo-list"]//child::li[2]`


![selenium_locators_xpath_devtools_1.png](/img/selenium_locators_xpath_devtools_1.png)

![selenium_locators_xpath_devtools_2.png](/img/selenium_locators_xpath_devtools_2.png)



## Additional resources

For more information and examples take a look at the following resources:

[MDN CSS selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors)

---


![dilbert_selenium_css.png](/img/dilbert_selenium_css.png)