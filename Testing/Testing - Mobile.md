> *Don’t just fix the bugs. Fix whatever permitted the bugs in the first place.*

## Summary

This article is a compendium of useful tips & tricks for testing mobile apps.

**General**

- <a href=#basics>Basics</a>
- <a href=#selecting-test-devices>Selecting test devices</a>
- <a href=#testing-biometrics>Testing biometrics</a>
- <a href=#testing-facebook-analytics>Testing Facebook analytics</a>
- <a href=#testing-valid-iban-numbers>Testing valid IBAN numbers</a>

**Android**

- <a href=#changing-the-rom-on-pixel-devices>Changing the ROM on Pixel devices</a>
- <a href=#devices-supported-by-google>Devices supported by Google</a>
- <a href=#donand39t-keep-activities>Don't keep activities</a>
- <a href=#enabling-developer-options>Enabling Developer options</a>
- <a href=#getting-nice-device-logs>Getting nice device logs</a>
- <a href=#how-to-download-a-beta-version-of-the-app-on-android>How to download a beta version of the app on Android</a>
- <a href=#how-to-fake-your-location-on-android>How to fake your location on Android</a>
- <a href=#installing-an-app-from-a-foreign-google-play>Installing an app from a foreign Google Play</a>
- <a href=#setting-up-an-android-emulator>Setting up an Android emulator</a>

**iOS**

- <a href=#enabling-ios-dev-settings>Enabling iOS dev settings</a>
- <a href=#installing-an-app-from-a-foreign-app-store>Installing an app from a foreign App store</a>
- <a href=#testing-production-builds-on-ios>Testing production builds on iOS</a>
- <a href=#how-to-install-iphone-or-ipad-apps-on-m1-mac>How to install iPhone or iPad apps on M1 Mac</a>


## General

### Basics
Have a look at an one of our blog posts on [testing mobile apps](https://infinum.co/the-capsized-eight/10-app-testing-principles).

### Selecting test devices

You cannot test your app on all possible devices. That is why it is important to intelligently decide on a set of devices on which you will do you your testing.

The two major mobile operating systems are:

- Android
- iOS

Some parameters to keep in mind:

- The minimum supported OS version (varies from project to project)
- The current OS version
- What the intended audience uses
- Screen size and resolution
- Chipset

For instance, if you had time to test a Croatian mBanking Android app on a mobile device, it would make sense to have:

- A current large flagship Samsung or Huawei device
- A smaller mid-range device which is two or more years old
- An old device running the minimum supported OS version

The device usage percentages of our apps can be retrieved from the Google Dev Console or iTunes Connect. Contact your team lead to get that info.

The usage of particular devices in general can be found on web sites such as [StatCounter](http://gs.statcounter.com/vendor-market-share/mobile).

Device-wise, make sure to use:

- Smartphones
- Tablets (if the project supports it!)

Browsers that will almost always fit the criteria in a mobile environment are:

- Chrome (Android)
- Safari (iOS)

Another important parameter in testing is orientation:

- Portrait
- Landscape

### Testing biometrics
When you test Android and iOS apps which allow the user to login with TouchID (iOS) or fingerprint (Android), you should check the following cases when the fingerprint login is enabled in the app:

- WHEN a new fingerprint is added to the currently saved fingerprint(s) in the phone's settings, THEN a "Fingerprint settings were changed" message should appear when logging into the app to reactivate the fingerprint login
- WHEN one of multiple saved fingerprints is deleted, THEN a "Fingerprint settings were changed" message should appear when logging into the app to reactivate the fingerprint login 
- WHEN all fingerprints are deleted, THEN a "Fingerprint disabled" message should appear when logging in and the fingerprint login toggle should be disabled in the app settings

When testing iOS apps which allow the user to log in with FaceID, you should check the following cases:

- WHEN none FaceID scan is saved in the phone's settings, THEN the FaceID toggle in the app settings 
should be turned OFF and disabled
- WHEN a FaceID scan is added and the FaceID permission is given for the app, THEN the FaceID toggle in the app settings should be enabled
- WHEN a FaceID scan is added and the FaceID permission isn't given for the app, THEN the FaceID toggle in the app settings should be turned OFF

### Testing Facebook analytics

Ensure Facebook SDK is implemented in the application, and that those analytics are set up correctly.

Find FacebookID of the account which you will use for testing. There are two ways of finding this ID, you either login to FB account and click on your profile name in the top left. Your ID will be visible in URL in the browser.

Facebook Analytics Admin needs to add this account to Facebook analytics. Account must be verified; otherwise, it cannot be added. 

1. Go to [developers.facebook.com](https://developers.facebook.com/)

2. Click **My apps** in top right corner and select app you want to test from the dropdown menu.
From the dashboard, click on **View analytics**. On the left side, click on **Activity** and then on **Events** 

By default, Facebook tracks standard events such as **App install** and **App launch**. You can find events that are tracked out of the box by default and list of standard events [here](https://developers.facebook.com/docs/app-events/getting-started-app-events-ios#auto-events).

**How to test?**

See implemented platforms, check which event is implemented and its requirements. Then try to trigger that event, and if everything is done correctly, the event should show up on the event screen mentioned above.

Facebook analytics dashboard will not show triggered events instantly.

### Testing valid IBAN numbers
Check out the list of valid [IBAN numbers](https://ssl.ibanrechner.de/sample_accounts.html) if you test your application's IBAN validation and make payments through the app using (foreign) IBAN numbers.


## Android

### Changing the ROM on Pixel devices

1. Use a Windows PC, it's easier
2. Visit the page [https://toolaio.tk/](https://toolaio.tk/)
3. Click the Download tab and download the .zip file
4. Extract the .zip file and install the app
5. Grab you Pixel device
6. Ensure the device has Developer options turned ON (if not, click the Build number in the phone's Settings 5 times in a row)
7. Open the Developer settings and turn ON OEM update and USB debugging
8. Connect the Pixel device with your PC
9. The dialog "Trust device?" will appear, click "Allow"
10. Open the "TOOL ALL IN ONE" app on your PC
11. Ensure the Pixel device is listed
12. Click the "Unlock" button under the "Bootloader" section. This step will reboot the device
13. After device is turned ON, it could be that you'll need to setup everything again
14. Open the "TOOL ALL IN ONE" again, and click the "Flash Factory Image" under the "Other options" section
15. Click the "Download Stock Rom" button and find the image you need (it will bring the page based on connected device. In our case, the list of stock Android versions (OEM) will appear)
16. Download the zip and without unzipping it, open the "TOOL ALL IN ONE" again
17. While you're on the "Generic Fastboot Rom Flasher" dialog, click the "[...}" button
18. Find the location where the zip is stored and click select
19. Click "Flash Rom"
20. After this step, the desired Android version will be installed on a device
21. As a final step, you should lock the bootloader by clicking the "Lock" button in the app

### Devices supported by Google
Find them [here](https://support.google.com/googleplay/answer/1727131?hl=en).

If a device is not on this list, we usually cannot guarantee it is fully supported either.

### Don't keep activities
A good practice when testing Android apps is to thoroughly circumnavigate the app with the "Don't keep activities" option enabled.

Users will usually not have this enabled, but it might point to issues that happen when the operating system decides to kill your activity, which it might do as part of its automatic memory management.

### Enabling Developer options
You can unlock the Developer options on any Android smartphone or tablet by locating the Build number in your Settings menu and tapping it multiple times. 

The exact location of the aforementioned build number may differ depending on your phone’s manufacturer.


### Getting nice device logs

- You need to install pidcat: `brew install pidcat`
- You need a debug build
- Device has to be recognized (open Terminal, input `adb devices` and verify that the device is listed)
- You can start pidcat with `pidcat package.name`
- You can find the package name by searching every installed app with `adb shell 'pm list packages'` (or with the [Package name](https://play.google.com/store/apps/details?id=vjayraj.packagename&hl=en_US) application).

### How to download a beta version of the app on Android

1. Login to G+ community for beta testing with your @infinum.com account
2. Force close Google Play Store and delete the cache and data for it
3. Run TunnelBear or some other VPN and connect through the country that you need to work on desired app.
4. Run Google Play Store, accept the T&C and skip the payment info
5. Find the app and install it (log in, activate it, etc.)
6. Accept that you are a beta tester for the app (the best way is to open  https://play.google.com/apps/testing/package.name.of.theapp/)
7. Wait for a little while for the change to propagate to Google Play (mostly for a few minutes)
8. Go to Google Play page for the app and update it

### How to fake your location on Android

On Android you can use [Lockito](https://play.google.com/store/apps/details?id=fr.dvilleneuve.lockito&hl=en) or [FakeGPS](https://play.google.com/store/apps/details?id=com.lexa.fakegps&hl=en).

As always, iOS is a bit more complicated and deserves a special [guide](https://infinum.com/handbook/qa/tools/using-xcode-location-mocking).

### Installing an app from a foreign Google Play

In 1Password we have stored Google accounts for different countries:

1. Germany
2. USA
3. Austria
4. Netherlands
5. Slovenia


**Steps:**

1. First, make sure that you have installed some VPN client on your test device
2. Next, go to Settings —> (Users &) Accounts and delete all Google accounts
3. Then go to Settings —> Apps —> Google Play Store —> Storage —> Clear data - basically, delete cache for Play store
4. Open your VPN client and connect to an appropriate country
5. Login with appropriate Google account:

    1. Settings —> Users & accounts
    2. Agree with T&C and accept back up
    
6. Open Google Play Store
    1. Find your app & click Install
    2. When Complete account setup appears, click on Continue then Skip
7. After you’ve installed the app, delete the appropriate Google account & log in with our test account

8. That's it, enjoy testing your app!

### Setting up an Android emulator

We usually do not test apps on emulators, but sometimes they can come in handy.

To get an Android emulator, do the following:

- Download Android Studio: https://developer.android.com/studio/index.html
- Install it and during installation make sure "Android Virtual Device" is selected
- Run Android Studio and do not import any settings
- Choose the Standard setup - the Emulator and SDK Tools will be downloaded automatically
- Start a new Android Studio project and use the default names if you wish
- Use the default form factors and minimum SDK settings (you won't be needing that)
- Use the default activity and activity name (you won't be needing that)
- Once Android Studio finishes loading the project, click on "Install missing platform and sync project" or "Install Build Tools" until Android Studio stops reporting error message at the bottom
- Go to View > Toolbar to get the toolbar
- On the toolbar click on the AVD Manager icon
- Click on Create Virtual Device...
- Select a device, e.g. Nexus 5X
- Click on Next
- Download a system image, e.g. API level 25
- Select a system image you just downloaded and click on Finish
- Click on the play icon to start the emulator
- Drag and drop the APK to the emulator

## iOS

### Enabling iOS dev settings
1. Open Xcode and connect your phone with an USB cable
2. Open Settings on your iOS device
3. Scroll down and tap ON "Developer"

### Installing an app from a foreign App store

In 1Password we have stored Apple accounts for different countries:

1. Germany
2. USA

**Steps:**

1. First, launch App store & tap on Apple ID (your avatar in the top right corner) & Sign out
2. Then, open Settings, tap on General --> Language & Region --> Region & select the appropriate country
3. Open the App store & once again click on your avatar in the top right corner & sign in with the aprropriate Apple ID account
4. Type in the app you are looking for
5. Click on Get & enjoy testing your app
6. Don't forget to repeat step #1 & sign in with our regulard test account

### Testing production builds on iOS

The file that actually gets uploaded to iTunes Connect cannot be installed on a development device since it first has to be signed by Apple. 

This means that "Production" builds on Tryoutapps are not identical to what actually ends up on the App Store, only those that you get via Testflight are. 

That's why you should make sure to always independently verify Testflight builds before they are published to users.


### How to install iPhone or iPad apps on M1 Mac

New Apple desktop devices with M1 chips have a neat ability to install any iPhone or iPad apps on the M1 Macs. This is possible due to the common architecture shared by the two operating systems. The only way to install apps that are made for iPhone or iPad is to download them directly through the AppStore!

**No porting required!**

iPhone and iPad apps on the App Store are automatically available on the Mac App Store on Apple silicon Macs, there is no need to modify the app. The same frameworks that your apps use on iPhone and iPad are available and tuned just for Mac, taking advantage of the same shared architecture.

**Here’s how you can download an app to install on an M1 mac:**

1. Open the ‌Mac App Store‌ and click your profile from the bottom-left of the page.
2. Click ‘iPhone‌ & ‌iPad‌ Apps’ tab situated under Account.
3. Select the app from the list and click the download button.

Once the app downloads, you can access it from the Launchpad or the Applications folder.

<span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:80%;">![M1_iphone_apps](/img/M1_iphone_Apps.png)</span>

> Some of the apps that you see in the ‌Mac App Store‌ are labeled with a warning that says "Not Verified for macOS," these apps are not optimized for use on a Mac.

**Mac App Store availability**

By default, apps are published automatically on the Mac App Store. App availability can be managed at any time in App Store Connect.

**Circumventing the App Store or "sideloading" apps**

Apps could be downloaded and installed via a third-party app (sideloaded) but Apple has disabled this feature on M1 Macs running macOS Big Sur 11.1 or newer. Currently, the only way to install the iPhone or iPad app on the M1 machine is to download it through the App Store.
