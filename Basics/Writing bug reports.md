> *People like consistency. Whether it's a store or a restaurant, they want to come in and see what you are famous for.*

Follow these general rules when producing bug reports.

The most important thing is to keep your bug reports consistent, especially within the scope of a single project. This allows other project members to easily scan your bug reports and facilitates their understanding.

This guide was written with Productive in mind. Other project management tools might employ additional fields, but the gist is the same.

Each bug report, at a minimum, consists of a title and a description.

## Title

The title can either be:
- An imperative denoting what needs to be done.
	- E.g. "Add an Info button to the login screen"
- Or a description of the error.
	- E.g. "The app crashes when I take a photo of myself"

## Description

Here user should describe short introduction to the bug where developers already could assume what is the main issue.

## Device/OS/App version info:

The device could be any type of machine that is used during testing.
E.g. “mobile device, computer, car display, home appliance”

OS could be any piece of software the user is operating at times  
E.g. “some car OS, tv OS, Firmware of appliances if needed, mobile OS, etc.”

In the App Version/Build field - name the build on which you managed to reproduce the issue. Add the environment when needed same as URL or File of request/cURL.  
E.g. “development environment, production environment, release candidate version of the app and their version”

> Device: Pixel 8 (Android 14)
> Version/Build: 2.0.1
> Environment: Development

or

> Device: MacBook Air (macOS 14.1.2)  
> Version/Build: 3.2.2  
> Browser: Safari 17.1.2  
> Environment: Production

### Prerequisites

In this section, address any information needed to reproduce before actually reproducing the issue, usually some specific state of the app, user roles, appliances, specific language settings, time of the day, etc.

If there is nothing specific to add before it, sometimes simply “User is logged in or Guest user” is enough and some information is provided.

> Prerequisites:  
> tester@infinum​.hr

### Steps to reproduce

In this section, describe step-by-step instructions that could reproduce the app every time, so developers could easily and quickly discover the bug itself.
Actual results:
 + Bonus tip: If the bug is more complicated, don’t let the developer fall in the trap so the developer can’t reproduce the issue. Write steps for cases when the issue is not reproducible if there are flows that are similar but not right in order to reproduce the bug.

> Steps:  
> 1. Start the app and log in  
> 2. Tap on the "Create new recipe" button  
> 3. Don't enter all mandatory data
> 4. Tap Save
> 5. Observe

### Actual results

In the "Actual" section, describe what happens once the described steps are executed. This is the "bug" itself.

> Actual results:  
> Recipe is saved without a warning that some fields are missing.

### Expected results

In the "Expected" section, describe the expected behavior. This part can sometimes be omitted. For instance, if you are reporting a crash, it is self-explanatory that the app should not be crashing.

Also, the expected behavior is always good to prove with:
- the Design link
- Task where original behavior is implemented
- Issue that caused the current issue
- Test case etc.

> Expected results:  
> Field that is not filled should be marked and user should not be able to create recipe without all mandatory fields.

### How to resolve

At times, it happens that the bug is recoverable from the bug state, this needs to be stated here.

> How to resolve:  
> Go back to the Home Screen to recover from the blocked state, etc.

### Reproduction rate

In the “repro” section, add a number that indicates how serious and in what percentage the bug is reproducible. 

Sometimes it happens that the bug is a serious bug but only 10% of users can reproduce it and then the impact is marked as low.

> Reproduction rate:  
> 2/5 = 40%, 5/5 = 100%

### Account info

Account info refers to the account used while reproducing the bug, It is handy to share it so developers can use this account and not create a new one.

One account could be connected to some appliance or some special configuration of the users that will save time in fixing bugs, etc. 

> Account info:  
> tester@infinum​.hr / Germany

### Additional notes

It is helpful to address what is attached in the bug report in order to reproduce the bug more quickly like: app logs, crash logs, screen recording, and screenshots. Strive to attach screenshots and screen recordings every time.

> Note:  
> Screen recording; screenshot attached; Crashlytics; Logs file; Request file attached

A full bug report for mobile app would look like this:

>Title
> User added Recipe to Favorites but tab is not refreshed right away

> Device/OS/App version info:  
> iPhone 15 Pro (iOS 17.2)
> Dev build 3.1.1

> Prerequisite:  
> There are already Recipes in the Favorites tab

> Steps to reproduce:  
> 1. Start the app and log in  
> 2. Browse Recipe  
> 3. Choose one  
> 4. Tap on Favorite button  
> 5. Go back to the Recipe tab  
> 6. Observe  

> Actual results:  
> Recipe is not added to the Favorites tab right away

> Expected results:  
> Recipe should be added when you return from Recipe details to Favorites tab

> How to resolve:  
> Kill the app and open again

>Reproduction rate:  
> 5/5 = 100%

> Account info:
> tester@infinum​.hr / Germany

> Additional notes:  
> Screen recording attached      
> Stack trace: fabric.io/crash

Additionally, never forget to:   

- Assign the task to someone
- Put bug to correct Sprint/Backlog
- Address correct priority and severity tag to the bug
  - Priority: Urgent, High, Medium, Minor, Low
  - Severity: Cosmetic, Minor, Major, Crash/Data loss, Safety
- Add tags (usually platform-related tags such as "Android" or "iOS").

Read more on the topic [here](https://infinum.co/the-capsized-eight/how-not-to-suck-at-writing-bug-reports).