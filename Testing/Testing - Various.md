> *Software and cathedrals are much the same: first we build them, then we pray.*

## Summary

This potentially infinite list is just some minor testing tidbits we gathered through the years that might help you find some sweet, sweet bugs.

- <a href=#android-vs-ios>Android vs iOS</a>
- <a href=#cert-pinning>Cert pinning</a>
- <a href=#compare-to-design>Compare to design</a>
- <a href=#could-your-grandmother-use-this>Could your grandmother use this?</a>
- <a href=#custom-time-and-date>Custom time and date</a>
- <a href=#empty-states>Empty states</a>
- <a href=#error-states>Error states</a>
- <a href=#get-a-crowd-to-help>Get a crowd to help</a>
- <a href=#get-a-designer-to-help>Get a designer to help</a>
- <a href=#get-a-tester-to-help>Get a tester to help</a>
- <a href=#get-off-the-beaten-path>Get off the beaten path</a>
- <a href=#hanging-calls>Hanging calls</a>
- <a href=#heuristics-in-general>Heuristics in general</a>
- <a href=#light-vs-dark-mode>Light vs Dark mode</a>
- <a href=#long-lists>Long lists</a>
- <a href=#lose-your-finger>Lose your finger</a>
- <a href=#monkey-testing>Monkey testing</a>
- <a href=#no-internet-connection>No internet connection</a>
- <a href=#orientation>Orientation</a>
- <a href=#permissions-just-say-no>Permissions? Just say no!</a>
- <a href=#prioritize-testing>Prioritize testing</a>
- <a href=#security-smoke-test>Security smoke test</a>
- <a href=#several-screen-sizes-aspect-ratios>Several screen sizes / aspect ratios</a>
- <a href=#submitting-a-form-with-missing-data>Submitting a form with missing data</a>
- <a href=#switching-between-mobile-data-and-wifi>Switching between mobile data and WiFi</a>
- <a href=#taking-screenshots-and-screen-recordings>Taking screenshots and screen recordings</a>
- <a href=#testing-on-a-slow-internet-connection>Testing on a slow internet connection</a>
- <a href=#testing-purchases>Testing purchases</a>
- <a href=#the-floating-keyboard>The floating keyboard</a>
- <a href=#try-some-crazy-strings>Try some crazy strings</a>
- <a href=#try-various-unexpected-inputs>Try various unexpected inputs</a>
- <a href=#what-to-watch-out-for-when-testing-social-login>What to watch out for when testing social login</a>

### Android vs iOS
Comparative testing is always a good thing to do, it could illuminate a lot of issues quickly, and will help to compare implementations on Android and iOS directly.

### Cert pinning
The app uses cert pinning? Try a _man-in-the-middle attack_ with Charles and its root cert. No responses coming through? Good, the devs did their job.

### Compare to design
Whenever testing a new feature, make sure to compare it to the agreed upon design (most often found on Zeplin or on Invision).

Pay close attention to:

- Animations
- Colors
- Fonts, font sizes, font weight, font colors, etc.
- Gestures - swipe left to delete, swipe down to refresh, swipe to go back, etc.
- Gradient direction
- Line height
- Margins and paddings
- Missing elements
- Pixelization
- Press effects
- Shadows
- States - loading, empty, error, success, etc.
- Typos
- etc.

### Could your grandmother use this?
Not sure that all the UX nitty-gritty has been worked out ok? Try stopping a neutral person for a bit of hallway testing and have them try the feature out.

[Three to five people are the magic number for usability testing](https://www.invisionapp.com/inside-design/ux-usability-research-testing/) anyway.

### Custom time and date
Should the app work without restrictions if a custom time/date is set on the device? For example, in freemium games, there might be countdown timers for users to earn an achievement (e.g. get points). Check that it is not possible to set the time on the device to a point in the future in order to "hack" the game's timer and earn the achievement in advance, without waiting for the countdown to finish. 

### Empty states
All screens that display dynamic data (e.g. lists, results, profiles, etc.) should have an "empty state" if there is no data to display. Preferably, the empty state of the screen should also include a call to action along with some persuasive copy.

### Error states
Do all the errors shown in the app have user-friendly messages? An uninformative message like "Error" without any additional description doesn't tell the user what exactly happened. A short, user-friendly description of the error would boost the user experience.

### Get a crowd to help
You've got a lot to test and not enough time? Ask the entire team to test by creating a test plan and organizing a **testing session**. An example of a test plan for such a session can be found [here](https://docs.google.com/spreadsheets/d/1MXcV9V50YlWDtGMYVLwaRZ28-_wQHgqKMbezMpSF6b0/edit?usp=drive_web&ouid=107444839076709052775).

### Get a designer to help
When testing a design-heavy feature, go to your designer and go through the look and feel together. They will usually catch some issues that have not been implemented as designed.

### Get a tester to help
Try pair testing and invite a colleague to help you out. Double the eyes, double the fun, double the success.

### Get off the beaten path
Don't just follow what the task says. Do whatever you think a user might do. Do what a user might not do as well.

### Hanging calls
Whenever a network request is being executed (which is often indicated with a loader), try navigating away from that screen. If the developer has not handled this case, it might result in a crash because the app will try to select or add data to screen elements that are no longer allocated in memory.

### Heuristics in general
A heuristic is any approach to problem solving, learning, or discovery that employs a practical method not guaranteed to be optimal or perfect, but sufficient for the immediate goals. Read more about it [here](https://infinum.com/handbook/qa/testing/heuristics-in-testing).

### Light vs Dark mode
Does the app support light and dark mode? Try switching between the modes while using the app. Everything is displayed correctly? Great! :) 

### Locale
The German strings never fit. Make sure to do a smoke test in all supported languages.
Other than strings, differing formats may also break certain features, e.g. dates, currencies, time, etc.

### Long lists
Scroll down through several pages of a list. Enter the item and change it. Now go back. Is the list appropriately scrolled and updated? Good.

### Lose your finger
The app uses fingerprint login? Remove all stored fingerprints from the device.

### Monkey testing
Behave like a monkey, try tapping that submit button two or three times. Try tapping navigation buttons several times.
The [Monkey testing](https://infinum.com/handbook/qa/automation/mobile/automated-monkey-testing) chapter might also help.

### No internet connection
Try going through the app without an internet connection.
Better yet, try doing an action that will result in a network call and lose the connection in the middle of the process.

### Orientation
If the app supports both orientations, make sure to test all screens in both orientations. Try rotating the screen between transitions and see if anything fails.

### Permissions? Just say no!
Whenever an app asks for permissions, always say no. Even better, say yes and then say no. What happens?

### Prioritize testing
When doing smoke testing, test the major and critical features first because that's where the risky bugs usually hide.

### Security smoke test
Run an automatic security test using MobSF or QARK for mobile or OWASP ZAP for web.

See this [chapter](https://infinum.com/handbook/qa/tools/mobile-security-testing-tools) for more detail.

### Sessions
Log in and put the app into the background. Come back after the token expires.

### Several screen sizes / aspect ratios
A good habit to get into is testing the app on several screen sizes. Some common aspect ratios and resolutions can be found on [DeviceAtlas](https://deviceatlas.com/blog/most-used-smartphone-screen-resolutions).

### Submitting a form with missing data
If you have to enter a username and password, enter just a username and submit. Nothing happened? That's bad UX. You should know what's missing.

### Switching between mobile data and WiFi
Try switching between mobile data and WiFi while using an app. If the switches between networks don't happen during API call executions, then the session should stay active and no errors should occur.

### Taking screenshots and screen recordings
Some mobile apps don't allow to take screenshots or screen recordings because they contain sensitive data (e.g. mobile banking apps contain account info and personal data). If taking screenshots and screen recordings is disabled, check that it is not possible to make them using built-in or third-party apps. Additionally, you can check that the app's screen is blurred when viewing the app in the active/recent apps list.

### Testing on a slow internet connection
Try accessing screens with a very slow internet connection. See if the calls time out, and if they do not, can the user navigate away from screens.

You can use our own slow network in the office: QA-Kornjaca

On iOS, you can also enable network throttling in Developer settings on the device itself and skip our Kornjaca.

You can use Charles or Proxyman to the same effect on both platforms.

### Testing purchases

Some tips for testing:

1. Make sure that you test both good and bad information. 
2. If you are testing on production(please don't do this) communicate with the client so that they know that some "fake" purchases are going to be coming through.
3. If the app uses services such as Ayden or WebPay or similar, try using a credit card that has a form of 2-part authentication like a bank token.
4. Cash on delivery is rather hard to test. You can test in tandem with the client when a user chooses this option. Cash on delivery does not go through a service, rather the payment is collected when a user receives the ordered item.
5. Check what happens if you lose internet connection during payment process.
6. Check how the process acts on a slow connection.
7. What happens if you get a pop-up.
8. What happens if you close the app in the middle of the payment process.
9. Verify that you receive a receipt for the purchase, otherwise the payment should not go through.
10. If the app has a shopping cart, make sure to verify that changing items within it, does not negatively affect the payment process.
11. If there is tax calculation within the payment process, check how it is calculated and if it is applied well.

The most important thing here is to follow the client requests, because the client is going to end up with that payment process and is going to have to work with it. Think of the users :)

### The floating keyboard
On an input field, get the keyboard up. Now go to the previous screen. Still up? Well that's a bug.

### Try some crazy strings
See the [Big list of naughty strings](https://github.com/minimaxir/big-list-of-naughty-strings) and the [Bug Magnet](https://bugmagnet.org/).

### Try various unexpected inputs
- Enter a number or string that is too big.
- Upload a file that is too big.
- Upload a wrong image, audio, video or document format.
- etc.

### What to watch out for when testing social login
A lot of the users today like having only one account for all the web places they visit, so more and more websites add the option to log in through things like Facebook, Google, Twitter and many more. The login testing by itself is no easy task, and the social media part just adds more complexity to it. Some of the stuff to watch out for is listed here:

- The login is usually the real first impression a user gets from a website. It's really important that there are no issues here, as a lot of the userbase will be put off by a bad login functionality.
- Use a combination of positive and negative tests to pull the login process through as many scenarios as possible.
- Test all versions of the login that the app will use, and don't forget about the old fashioned registration and login form.
- Make sure that, if there are any redirects, they redirect to the correct URL. Don't want your users to get lost once they are logged in :D
- Always check the API calls the login uses. Stuff could be in plain text in there and you really, and I mean really, do not want that.
- Check what is saved into the database with a dev. You can usually find a lot of funky stuff in the early stages of a project.
