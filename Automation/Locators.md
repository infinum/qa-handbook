> *Deleted code is debugged code.*

## Which locator to use?

It seems pretty straightforward: "simply copy the locator and put it into your code".
Just in case you try to find the best locator ever and decide to go online to search for some useful information.

Firstly, you might come across blog posts and articles naming different locators without saying much about them.
Secondly, you read about people having different opinions. For some, ID is the best approach, others prefer Accessibility ID, and then there are those that only use XPath.
Thirdly, you hear people arguing about which one is faster, as if difference is measured in days and not milliseconds.

However, there is more to think about when choosing the right locator, and it doesn't matter whether you like the looks of it or whether is it slightly faster the other ones.

Which one to choose?
Generally speaking, just go with the most reliable one. 
If it works 100% of the time (always returns the correct element), is less prone to change (you don't need to update it often or at all), and does not break or slow down your tests drastically, that's the one.


## A bit more about locators
### ID

ID will often be unique which makes it a great choice. It is often used by developers and might already be present in many places.

However, it might not always be unique. If we are talking about Appium (mobile), ID is `resource-id` (android) / `name` (iOS).
In a list, all elements might have the same ID. In that case, you will have to iterate over the list to find the correct element. Or try using another locator which won't require additional code.

TODO ADD EXAMPLE

### Accessibility ID
Sometimes you might come across an information how the Accessibility ID is a preferred locator strategy because it can be used for cross-platform automation making the code reusable.
However, what is often not mentioned is that the Accessibility ID is just a string, susceptible to change. 
This can especially become an issue if you have a lot of hardcoded locators in your code.

Where the Accessibility ID comes in very handy are lists of elements. If you have a list of movies and what to get the specific one, you can locate it through its title, without having to write loops yourself.

    def get_movie_by_title(self, movie_title):
        title_locator = {
            config.ANDROID: (MobileBy.ACCESSIBILITY_ID, "movie_title"),
            config.IOS: (MobileBy.ACCESSIBILITY_ID, "movie_title")
        }

        return self.get_present_element(title_locator[config.PLATFORM])
   

Accessibility ID is very useful, but it is above all used for [accessibility](https://www.w3.org/standards/webdesign/accessibility) and not for test automation.

### XPath and CSS
- zajedno kako bi ukratko opisao da moraju lijepo izgledati i biti jasni
- odvoji ako bude potrebno


List of elements

def get_profile_description_by_description(self, profile_description):
    list_of_descriptions = self.list_of_profile_description

    for description in list_of_descriptions:
        if description.text == profile_description:
            index = list_of_descriptions.index(description)
            return self.list_of_profile_description[index]

    return None


## Naming differences


| Appium | Android | iOS |
| :--- | :--- | :--- |
| Accessibility ID | content-desc | accessibility-id |
| ID | resource-id | name |

If you open XCode Accessibility Inspector
 - on the Inspector the a11y ID will be under the **Identifier** property


### Requesting new / additional locators
When adding new IDs or requesting the developers to add them, there are a few things to consider.
On which element do you want to have the ID added?
Will the developer be able to add the ID to the desired element?
    - it gets tricky, for example, when adding an ID to a LayoutView which holds multiple text elements
    - you might not be happy with the result and the ID will have to be updated (moved to another element)

---



