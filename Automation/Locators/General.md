> Deleted code is debugged code. - Jeff Sickel

## Which locator to use?

It seems pretty straightforward: "copy the locator and paste it into your code".
Just in case, you decide to go online to search for some useful information in hope to find the best locator strategy ever. 
First, you come across blog posts and articles naming different locators without saying much about them.
Then, you read about people having different opinions. For some, ID is the best approach, others prefer Accessibility ID, and then there are those that only use XPath.
Finally, you hear people arguing about which one is faster, as if the difference is measured in days and not milliseconds.
And now you are confused.

Which one to choose?
You want the most reliable one, pretty much regardless of the strategy. If it works 100% of the time (always returns the correct element) that is it. 
Generally, the most reliable one is less prone to change (you don't need to update it often, or at all), and does not slow down your tests execution time too much compared to other strategies.


## A bit more about locators

### ID

_ID_ is mostly unique which makes it a great choice. It is used by developers and might already be present on most elements.

It might not always be unique. 
In a list of items, all elements might have the same ID (that is, `resource-id` (Android), `accessibility id` / `name` (iOS)).
In that case, you have to iterate over the list to find the correct element. Or try using another strategy which won't require additional code, such as finding the element by Accessibility ID.


### Accessibility ID

You might come across information how the _Accessibility ID_ is a preferred locator strategy because it can be used for cross-platform automation making the code reusable.

However, make sure you understand what is being used. When using _Accessibility ID_ strategy, Appium looks for `ContentDescription` on Android, and both `AccessibilityLabel` and `AccessibilityIdentifier` on iOS. `ContentDescription` and `AccessibilityLabel` define labels (text) that is shown in the UI. Labels are susceptible to change. If the label changes, you also have to update your locators. This can especially become cumbersome if the changes happen regularly and if you only rely on this locator strategy.

The _Accessibility ID_ comes in very handy when there are lists of elements without unique ID on each element. 
For example, if you have a list of movies and want to get the specific one, you can locate it through its title, without having to write loops.

```python
def get_movie_by_title(self, movie_title: str):
    title_locator = {
        ANDROID: (AppiumBy.ACCESSIBILITY_ID, movie_title),
        IOS: (AppiumBy.ACCESSIBILITY_ID, movie_title)
    }

    return self.get_visible_element(title_locator[config.PLATFORM])
```

**NOTE:** 

- Check the [Naming differences](https://infinum.com/handbook/qa/automation/locators/general#naming-differences) section for more info on Accessibility ID and terminology differences between Appium and mobile platforms.
- Make sure you are not abusing `accessibility id` since it is primarily used for [accessibility](https://www.w3.org/standards/webdesign/accessibility) and not for test automation.


### XPath

XPath is very useful when you don't have an ID nor Accessibility ID in the app. Or when it would take too long for the developers to add them, and you really want to finish your test.
There is also nothing wrong with using XPath as your first choice.

What you want to be careful about is making it difficult to understand, long, and therefore unmaintainable. 
Another potential problem with XPath is that it might break even due to a minor change in the app.

Bad:

`//table[contains(@class , 'table-striped')]/descendant::td[7]`

Very bad:

`/html/body/div[2]/div[1]/h4[1]/html[1]/body[1]/div[2]/div[1]/div[1]/h4[1]`


Don't go blindly copy-pasting the locator from an inspector or DevTools. Learn a thing or two about XPath and how to write your own.

Better:

`//input[@id='new-todo']`

Read the [Selenium locators - XPath](https://infinum.com/handbook/qa/automation/locators/xpath) article for more details.


### CSS selector

For CSS selectors similar points apply as for the XPath.
You don't want just to copy-paste them from the DevTools and you also don't want to be too specific.
Tweak them a bit to make them more readable and maintainable.

Bad:

`#container .dashboard-advanced-reports .dashboard-advanced-reports-description .dashboard-advanced-reports-title`

Better:

`#login-form .sign-in-button`


## Inspecting elements

### Web

When working with a web app, use the browser's developer tools to inspect the page.
All browsers have this kind of tool.
Check out [Chrome Dev Tools](https://infinum.com/handbook/qa/tools/using-chrome-dev-tools) for more details.

### Mobile

To find the locator and attribute values of an element on mobile, you can use [Appium Inspector](https://github.com/appium/appium-inspector).

While inspecting an iOS app with Appium Inspector, you might come across some issues, like not being able to see the element properly. 
In that case, try using the Xcode Accessibility Inspector.
Accessibility Inspector shows the _Accessibility ID_ under the **Identifier** property.

Open Accessibility Inspector:

1. Open _Xcode_
2. Select _Xcode_ in the upper left corner
3. Select _Open Developer Tool_ 
4. Select _Accessibility Inspector_

While in the Accessibility Inspector, select the device you want to inspect in the upper left corner.


## Naming differences

There are some naming differences that add to the confusion when comparing Appium, Android and iOS terminology.

### AppiumBy.ID

When locating an element using **AppiumBy.ID**, Appium looks for `Resource ID` value on Android, and `AccessibilityIdentifier` on iOS.

When inspecting the app using Appium Inspector you will see attributes:

- `id` and `resource-id` showing the value of `Resource ID` (Android)
- `accessibility id` and `name` showing the value of `AccessibilityIdentifier` (iOS)


### AppiumBy.ACCESSIBILITY_ID

When locating an element using **AppiumBy.ACCESSIBILITY_ID**, Appium looks for `ContentDescription` value on Android and both `AccessibilityLabel` and `AccessibilityIdentifier` on iOS. 

When inspecting the app using Appium Inspector you will see attributes:

- `accessibility id` and `content-desc` showing the value of `ContentDescription` (Android)
- `accessibility id` showing the value of `AccessibilityLabel` or `AccessibilityIdentifier`, `name` showing the value of `AccessibilityIdentifier`, and  `label` showing the value of `AccessibilityLabel` (iOS)

Using `AppiumBy.ACCESSIBILITY_ID` might seem a bit confusing, especially for iOS. Just think of it as using a visible text to get an element.


Hopefully the table makes things a bit clearer. It shows the values that you get depending on the locator strategy that you use. Android and iOS columns show the values implemented in the app.

| Locator strategy | Appium Inspector   | Android            | iOS                                          |
|:-----------------|:-------------------|:-------------------|:---------------------------------------------|
| ID               | id                 | Resource ID        |                                              |
| ID               | resource-id        | Resource ID        |                                              |
| ID               | name               |                    | AccessibilityIdentifier                      |
| ID               | accessibility id   |                    | AccessibilityIdentifier                      |
| ACCESSIBILITY_ID | accessibility id   | ContentDescription | AccessibilityLabel / AccessibilityIdentifier |
| ACCESSIBILITY_ID | content-desc       | ContentDescription | AccessibilityLabel                           |
| ACCESSIBILITY_ID | label              |                    | AccessibilityLabel                           |


**NOTE:**

- Appium documentation mentions `name` as a native element identifier that Appium looks for when finding an element by ID on iOS. However, iOS does not have the `name` attribute. To set the ID, the iOS uses [AccessibilityIdentifier](https://developer.apple.com/documentation/uikit/uiaccessibilityidentification/1623132-accessibilityidentifier)

- if `AccessibilityLabel` has the same value as `AccessibilityIdentifier`, Appium will match two elements since both are recognised by Appium as `accessibility id`
  - [AccessibilityLabel](https://developer.apple.com/documentation/objectivec/nsobject/1615181-accessibilitylabel) is used by screen readers and should be written in a user-friendly manner
  - `AccessibilityIdentifier` should use a different format to avoid confusion and retain uniqueness


## Requesting new / additional IDs

When adding new IDs, there are a few things to consider:

- On which element do you want to have the ID added?
- Is developer able to add the ID to the desired element?
- What should the ID look like?

It gets tricky, for example, when adding an ID to a LayoutView which holds multiple text elements. The result might not be what you expected.
To avoid such issues, ask a developer to add a few as an example to see what it looks like.

### Plan your work

When requesting new IDs, don't request a bunch from different parts of the app all at once. You might realise they were put in the wrong place or end up not using them. It will also take too much time to add all of them, and some might be left out. 

Plan out your work. You could divide the sections of the app you want to cover per sprint. For example, in Sprint 1 you want to cover feature-1. Then in Sprint 2 you want to focus on feature-2.
With that figured out, open a few tasks for developers asking for IDs needed in those features. Creating more specific tasks will make the process of adding IDs and verifying they are in the app much faster.

Since you are already doing automation on your project, the process can be improved a bit more.
One of the acceptance criteria for new features could be adding IDs needed for test automation. That doesn't have to be extensive. Simply adding IDs on buttons and input fields that are most likely to be used for test automation is a great start.
The developer has to add those elements anyway, so a few more lines of code won't be too cumbersome and the feature will be at least partially ready for automation from the start.

### Platform differences

It would be quite convenient if locators look the same on all the platforms you are running your tests on.
For example, the ID on both Android and iOS for the submit button could be `Submit`.

What would further make everyone's work easier is having a table, a Figma page or some other document with a list of defined IDs. That way, a developer could just check how the ID should look like for the specific element and add it. 
Thus, you won't have to constantly inspect elements and the IDs would look the same across multiple platforms.

Of course, it won't be possible to have the same locator values for every element, but it will probably work for most.
