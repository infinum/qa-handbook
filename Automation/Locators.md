> Deleted code is debugged code. - Jeff Sickel

## Which locator to use?

It seems pretty straightforward: "copy the locator and paste it into your code".
Just in case, you decide to go online to search for some useful information in hope to find the best locator strategy ever. 
First, you come across blog posts and articles naming different locators without saying much about them.
Then, you read about people having different opinions. For some, ID is the best approach, others prefer Accessibility ID, and then there are those that only use XPath.
Finally, you hear people arguing about which one is faster, as if the difference is measured in days and not milliseconds.
And then you get confused.

Which one to choose?
Generally speaking, just go with the most reliable one. 
If it works 100% of the time (always returns the correct element), is less prone to change (you don't need to update it often or at all), and does not break or slow down your tests drastically, that's the one.

However, there is more to think about when choosing the right locator, and it doesn't matter whether you like the looks of it or whether it is slightly faster than the other ones.
Often you realise the issue when you come across it.

## A bit more about locators

### ID

ID will often be unique which makes it a great choice. It is often used by developers and might already be present on most elements.

But it might not always be unique. 
In a list of items, all elements might have the same ID (that is, `resource-id` in Android, `name` in iOS). 
In that case, you will have to iterate over the list to find the correct element. Or try using another locator which won't require additional code, such as Accessibility ID.


### Accessibility ID

You might come across information how the Accessibility ID is a preferred locator strategy because it can be used for cross-platform automation making the code reusable.
However, what is often not mentioned is that the Accessibility ID is a string, susceptible to change. If the UI and accompanied strings change, you will also have to update your locators.
This can especially become cumbersome if the changes often happen and if you only rely on that one locator strategy.

Where the Accessibility ID comes in very handy are lists of elements. If you have a list of movies and how to get the specific one, you can locate it through its title, without having to write loops yourself.

    def get_movie_by_title(self, movie_title):
        title_locator = {
            config.ANDROID: (MobileBy.ACCESSIBILITY_ID, "movie_title"),
            config.IOS: (MobileBy.ACCESSIBILITY_ID, "movie_title")
        }

        return self.get_present_element(title_locator[config.PLATFORM])
   

Accessibility ID is very useful, but it is above all used for [accessibility](https://www.w3.org/standards/webdesign/accessibility) and not for test automation.


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

Read the [Selenium locators - XPath](https://infinum.com/handbook/qa/automation/selenium-locators-xpath) article for more details.


### CSS selector

For CSS selectors similar points apply as for the XPath.
You don't want just to copy-paste them from the DevTools and you also don't want to be too specific.
Tweak them a bit to make them more readable and maintainable.

Bad:

`#container .dashboard-advanced-reports .dashboard-advanced-reports-description .dashboard-advanced-reports-title`

Better:

`#login-form .sign-in-button`


## Naming differences

When talking about mobile, there are some differences to take into account.

If we consider Appium:

- the **ID** in Appium is `resource-id` on Android and `name` on iOS.
- **Accessibility** ID in Appium is `content-desc` on Android and `accessibility-id` on iOS.

If you don't see the ID / Accessibility ID for your iOS app in Appium, consider using the XCode Accessibility Inspector.
There you will see the Accessibility ID under the **Identifier** property.


| Appium | Android | iOS |
| :--- | :--- | :--- |
| Accessibility ID | content-desc | accessibility-id |
| ID | resource-id | name |


## Requesting new / additional IDs

When adding new IDs, there are a few things to consider:

- On which element do you want to have the ID added?
- Will the developer be able to add the ID to the desired element?
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


---


![dilbert_automation_locators.png](/img/dilbert_automation_locators.png)

*Image downloaded from [dilbert.com](https://dilbert.com/strip/2022-02-08): 02-08-22 by Scott Adams*
