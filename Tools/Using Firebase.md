> *Everybody can do testing, but only a tester does good testing.*

## Testing Firebase push notifications

Ensure FCM is implemented in-app and that push notifications are set up correctly in Firebase.

Go to **[Firebase console](https://console.firebase.google.com/)**. Open project you want to test, be careful as you might have a choice between staging and production.
From the menu on the left, scroll down, and choose **Cloud Messaging**. Then click on **New notification** and begin to enter your parameters.

**STEPS:**

**1. Notification:** Enter mandatory and optional parameters you desire, basically how your push notification will look like.

**2. Target:** If the app you are using is set up to use topics, choose topics, and select topics available. Topics are implementation-specific, and target depends on implementation. If your app doesn’t have topics, use user segments. Select app or combination of apps you wish to target. These usually target the whole userbase with that package installed and on the selected platform. If you choose staging environment on an iOS app, everybody on iOS with that app installed will get the push notification.

**3. Scheduling:** Select Scheduling, do you wish to send your message now or at a specific time? You can also set recurring notifications.

**4. Conversion:** This is optional, selecting any conversion event will enable you to trigger push notification upon the specified event. Did the user opened the app for the first time or bought something inside in-app?

**5. Additional options:** Optional as well, you can add custom key-value pairs provided by your developer. For example: **“type”: “screen”** or **“location”: ”results”**

**6. Finally:** Click **Review** and then **Publish** from the modal window. Check your phone and verify push notification arrived with all parameters that you specified in steps above.


## Tracking Firebase events in real time

 
Generally, Events logged by our apps are batched together over the period of approximately one hour and uploaded together (this way we save the battery and reduce network data usage on users' device).

But, for the purpose of testing the analytics implementation, we can use Debug mode on a test device to upload Events with a minimal delay.

 
#### How to get Debug mode on your device?

**iOS**

Ask your favorite iOS developer to make you a Debug mode of the build that has analytics implemented (info how to implement the Firebase Debug mode can be found [here](https://firebase.google.com/docs/analytics/debugview) - iOS tab).
 
**Android**

You can ask your favorite Android developer as well, but this one you can make on your own - and it’s fairly simple (so be kind to Andys and do it :). Just follow the steps below:

1. First, you’ll need the ADB tool on Terminal. You can easily check if you already have it installed by connecting your Android device to your Mac and running command: adb devices. If you get a message saying that ADB is not installed go to step 2; else go straight to step 3.
2. To install ADB, follow these [steps] (https://stackoverflow.com/a/32314718/3939801), Option 1 (in case some homebrew permission issues are thrown in the console, check this [link](https://gist.github.com/irazasyed/7732946)).
3. To keep it simple, when following these steps, connect only one device to your Mac - it’s a bit more complicated when you have multiple devices.
4. Execute the following command in Terminal:
`adb shell setprop debug.firebase.analytics.app <package_name> `

**Tracking events**

After you have set it all up, open the Firebase console, select your project and in the side navigation select DebugView. If you have multiple devices with Debug mode enabled, you can use the Device selector in the upper left corner to choose the specific device on which you will be focused.
 
Then, just start using your app to see your app’s events being logged in the DebugView report. In the left column on the screen, you will see the Minutes stream that shows a series of archives of Events over the last 30 minutes. The Middle Stream will show you what you came here for - all Events triggered in the last 30 minutes. By tapping on a single Event, you can see the Parameters and User properties of each Event.

Be aware that Firebase automatically tracks some Events and ScreenViews since you’ll only be checking the custom ones. You can feel free to ignore the rest :)

You will probably have .xlsx file made by Data Analyst team with defined Events and Parameters - you need to make sure that all of them are implemented as defined and to compare the implementation cross-platforms.

While testing, please be precise. Here is a list of things that may go wrong (and, at some point, probably will):

- Are Events named the same cross-platforms? **They are case sensitive.**
- Are they triggered on the same place?
- Are they triggered as many times as it’s shown?
- Do the Events have the right Parameters (if custom Parameters are implemented)?

***Pro Tip:*** *When testing custom Parameters, if they are not shown the first time the Event is triggered, try to refresh the Firebase first, before reporting the bug. DebugView has some bugs there, sometimes it shows the Parameter only after the refresh. It will save you from reporting and cancelling bugs.*

Also, as always, your job is not only to check, but to improve - if you see some important things that are not being tracked (they are not even defined by Data Analyst), or any other illogicality, feel free to discuss it with Data Analyst and define new plan with them. Then ask the developer to implement the new plan.

If you need more info, check [this](https://firebase.google.com/docs/analytics/debugview) link.

---
![dilbert-analytics.jpg](/img/dilbert-analytics.jpg)

