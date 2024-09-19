## Naming differences

There are some naming differences that add to the confusion when comparing Appium, Android, and iOS terminology. Specifically, when using `AppiumBy.ID` and `AppiumBy.ACCESSIBILITY_ID`.

To help with understanding, it is useful to use Appium Inspector to visualize the differences.

Appium Inspector displays two useful sections on the right-hand side, Find By and Attribute.
- **Find By** shows (some) locator strategies you could use to find the selected element, and the value it returns
- **Attribute** provides information on the element's properties, and their corresponding values

![inspecting_android_app](/img/locators_android.png)


### AppiumBy.ID

When locating an element using **AppiumBy.ID**, Appium looks for the following atributes:

- `resource-id` (Android)
- `name` (iOS)


### AppiumBy.ACCESSIBILITY_ID

When locating an element using **AppiumBy.ACCESSIBILITY_ID**, Appium looks for the following attributes:

- `content-desc` (Android)
- `label` and `name` (iOS)


### Appium Inspector

When inspecting the app with Appium Inspector you see the available strategies shown in the **Find By** section, and element attributes in the **Attribute** section.

**Find By**

For Android

- `id` shows the value of `Resource ID`
- `accessibility id` shows the value of `ContentDescription`

For iOS

- `accessibility id` shows the value of `accessibilityLabel` or `accessibilityIdentifier`


**Attribute**

For Android

- `resource-id` shows the value of `Resource ID`
- `content-desc` shows the value of `ContentDescription`

For iOS

- `name` shows the value of `accessibilityIdentifier` (or `accessibilityLabel` if `accessibilityIdentifier` is not set)
- `label` shows the value of `accessibilityLabel`


### Table: Locator strategies in Appium Inspector

The table below shows different locator strategies used in Appium, and corresponding strategy shown in Appium Inspector, and properties that are set on mobile platforms.

| Appium Inspector   | Android            | iOS                                          |
|:-------------------|:-------------------|:---------------------------------------------|
| id                 | Resource ID        |                                              |
| accessibility id   | ContentDescription | accessibilityLabel / accessibilityIdentifier |


### Table: Element attributes in Appium Inspector

The table below shows different element attributes found by Appium, and corresponding values shown in Appium Inspector, as well as properties that are set on mobile platforms.

| Appium Inspector   | Android            | iOS                                          |
|:-------------------|:-------------------|:---------------------------------------------|
| resource-id        | Resource ID        |                                              |
| content-desc       | ContentDescription |                                              |
| name               |                    | accessibilityLabel / accessibilityIdentifier |
| label              |                    | accessibilityLabel                           |


**Note**:

- [accessibilityLabel](https://developer.apple.com/documentation/objectivec/nsobject/1615181-accessibilitylabel) is used by screen readers and should be written in a user-friendly manner
- `accessibilityIdentifier` should use a different format to avoid confusion and retain uniqueness


### Additional resources

Check [Mobile - element IDs](https://infinum.com/handbook/devproc/test-automation/mobile-element-ids) for info on how to set the element ID.
