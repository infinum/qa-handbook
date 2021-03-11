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

### Header - mobile apps

In the "Device" field - name those devices on which you managed to reproduce the issue.

In the "Build" field - name the build on which you managed to repoduce the issue. Add the environment when needed.

> Device: Nexus 5X (Android 7.0), HTC M9 (Android 6.0)   
> Build: 1.1.0-b4422 (Development)

### Header - web apps

The aforementioned is true for web apps, but you usually omit the build number and add the browser you used.

> Device: Nexus 5X (Android 7.0)  
> Browser: Chrome 66    
> Environment: Development

or

> Device: MacBook Air (macOS 10.13.2)  
> Browser: Chrome 67  
> Environment: Development    

### Prerequisites

In the "Prerequisties" section, state any info that is needed in order to start reproducing the issue. This might be the account you used, the role of the user, time of day, etc. 

This part is optional.

> Prerequisites:  
> Account used: <tester@infinum.hr>

### Steps

In the "Steps" section, describe a step-by-step procedure that you took in order to reproduce the issue.

> Steps:  
> 1. Start the app and log in  
> 2. Tap on the "Create new recipe" button  
> 3. Tap on the "Add recipe photo" button  

### Actual

In the "Actual" section, describe what happens once the described steps are executed. This is the "bug" itself.

> Actual:  
> The camera app is opened.

### Expected

In the "Expected" section, describe what is the expected behaviour. This part can sometimes be omitted. For instance, if you are reporting a crash, it is self-explanatory that the app should not be crashing.

> Expected:  
> A dialog should appear allowing me to choose between selecting a photo from the gallery and using the camera to take the photo.

### Note
> Note:
> Zeplin link: zpl.io/screen

In the "Note" section give any additional info that might be relevant: 

- State that screenshots or screencasts are attached to the task
- Add a Fabric/Invision/Zeplin link
- Refer to another task
- etc.

A full bug report would look like this:

> Title: Add a dialog for choosing the method of recipe image selection

> Device: Nexus 5X (Android 7.0), HTC M9 (Android 6.0)   
> Build: 1.1.0-b4422 (Development)

> Prerequisites:  
Clean install.

> Steps:  
> 1. Start the app and log in  
> 2. Tap on the "Create new recipe" button  
> 3. Tap on the "Add recipe photo" button

> Actual:  
> The camera app is opened and the app crashes.

> Expected:  
> A dialog should appear allowing me to choose between selecting a photo from the gallery and using the camera to take the photo.

> Note:  

> Design of the dialog: zpl.io/dialog      
> Stack trace: fabric.io/crash

Additionally, never forget to:   

- Assign the task to someone.
- Add it to the appropriate task list (usually backlog or shortlist, depending on the severity/priority of the issue).
- Add tags (usually platform-related tags such as "android" or "ios").

Read more on the topic [here](https://infinum.co/the-capsized-eight/how-not-to-suck-at-writing-bug-reports).

---

![writing-bug-reports.gif](/img/writing-bug-reports.gif)
