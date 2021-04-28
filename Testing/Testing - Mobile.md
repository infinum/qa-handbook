> *Don’t just fix the bugs. Fix whatever permitted the bugs in the first place.*

## Summary

This article is a compendium of useful tips & tricks for testing mobile apps.

**General**

- <a href=#basics>Basics</a>
- <a href=#installing-a-build-from-tryoutapps>Installing a build from Tryoutapps </a>
- <a href=#prerelease-checklist-for-mobile-apps>Prerelease checklist for mobile apps</a>
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
- <a href=#jailbreaking-ios11-with-uncover>Jailbreaking iOS11 with Uncover</a>
- <a href=#jailbreaking-ios12-with-uncover>Jailbreaking iOS12 with Uncover</a>
- <a href=#how-to-remove-jailbreak-on-ioS13.3>How to remove jailbreak on iOS13.3</a>
- <a href=#testing-production-builds-on-ios>Testing production builds on iOS</a>


## General

### Basics
Have a look at an one of our blog posts on [testing mobile apps](https://infinum.co/the-capsized-eight/10-app-testing-principles).

### Installing a build from Tryoutapps
1. Navigate to [Tryoutapps](https://infinum.tryoutapps.com/)
2. Open up the QR scanner on your phone (on iOS 11 and up, it is built into the Camera app)
3. Scan the QR code
4. Install the build

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

The device usage percentages of our apps can be on G theoogle Dev Console or on iTunes Connect. Contact your team lead to get that info.

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
Check out the list of valid [IBAN numbers](http://criticaltester.com/test-data/iban-values-testing/) if you test your application's IBAN validation and make payments through the app using (foreign) IBAN numbers.


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
20. After this step, the desired Androd version will be installed on a device
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

As always, iOS is a bit more complicated and deserves a special [guide](https://infinum.com/handbook/books/qa/tools/using-xcode-location-simulation).

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

### Jailbreaking iOS11 with Uncover

iOS jailbreaking is the privilege escalation of an Apple device for the purpose of removing software restrictions imposed by Apple on iOS, tvOS and watchOS operating systems.

It means giving apps admin (root) level access, which in term allows installation of other apps, tweaks and themes not on the App Store.

It supports the following iOS 11 versions: iOS 11, iOS 11.0.1, iOS 11.0.2, iOS 11.0.3, iOS 11.1, iOS 11.1.1, iOS 11.1.2, iOS 11.2, iOS 11.2.1, iOS 11.2.5, iOS 11.2.6, iOS 11.3, iOS 11.3.1 and iOS 11.4 beta 3.

**Requirements:**

- Make sure that you take a complete backup of your iPhone, iPad or iPod touch using iTunes
- Ensure that your device has enough battery level for the jailbreak process to complete
- Download the latest version of Uncover jailbreak IPA from Pwn20wnd’s [Github page](https://github.com/pwn20wndstuff/Undecimus) and Cydia Impactor from [here](http://www.cydiaimpactor.com/) on your Mac or PC. Cydia Impactor is available for macOS, Windows, Linux (32-bit and 64-bit)

**Steps:**

1. Install/Sideload Unc0ver IPA using Cydia Impactor

	 Connect your iPhone, iPad or iPod touch to the computer with the Lightning cable. 
	
	 Launch Cydia Impactor on your computer. It will detect your iOS device. Drag the Uncover jailbreak IPA file you had downloaded earlier on to its UI. Enter the Apple ID and password for your Apple Developer account when prompted, and wait for Cydia Impactor to sideload the signed app on your iOS device.

2. Trust Developer Profile

	 Once Uncover jailbreak IPA is successfully sideloaded. Launch the Settings app, and navigate to Settings > General > Profile(s) & Device Management (in some iOS versions it may just be General > Device Management).
	
	 Tap on the entry with your Apple ID under Developer app, then tap on Trust. Tap on the Trust button. The status will change to Delete app.
	
	 _Note_: This step is not required if you’ve used an Apple Developer account.

3. Enable Airplane Mode

4. Disable Siri

5. Reboot iOS device

	 After your device has rebooted, ensure that Airplane mode is still enabled, and also ensure Wi-Fi is disabled if it hasn’t got disabled while enabling Airplane mode.

6. Run Jailbreak Process

	 Launch the Uncover Jailbreak app from the Home screen, and tap the blue Jailbreak button to start the jailbreak process.

7. Wait for Jailbreak to complete

	Cydia should also be installed on your Home screen. You should be able to launch it and install the jailbreak apps and tweaks. If you don’t see Cydia on the Home screen, then reboot your iOS device and launch Uncover Jailbreak and keep trying until it works.
	
	You can also disable Airplane mode and re-enable Siri after your iPhone, iPad or iPod touch has been successfully jailbroken.
	
	The complete guide can be found [here](http://www.iphonehacks.com/2018/10/how-jailbreak-ios-11-unc0ver-jailbreak.html).
		
### Jailbreaking iOS12 with Uncover

There are many reasons to jailbreak iOS 12 such as to install iFile, which gives access to the file system, tweaks like Message Customizer that lets you customize each aspect of the Messages app, ability to lock apps and folders using Touch ID and lots more. You don’t even need access to a computer for the entire process.

You can download the latest version of Uncover jailbreak from [Github] (https://github.com/pwn20wndstuff/Undecimus/releases) hosted by pwn20wnd.

You can download the latest version of Chimera jailbreak from [here] (https://chimera.sh/) hosted by Electra team.

**Requirements**

- Delete any iOS 12 OTA update file from Settings -> Storage and reboot your device before attempting to jailbreak it. If an OTA file is present, your device will end up in a respring or reboot loop.
- Uncover jailbreak has complete support for Cydia and Substrate.
- Make sure to create a backup of all important data on your device before proceeding with the jailbreaking steps.

**Steps:**

1. Download Latest Uncover beta

	 Go to ignition.fun on your iPhone or iPad running iOS 12.4. Use the search bar to find Unc0ver. Tap on Get followed by Install. Wait for the app to download and install on your iOS device.
	 
	 <img src="http://cdn.iphonehacks.com/wp-content/uploads/2019/08/unc0ver.jpg" alt="UncOver" style="display: block; margin-left: auto; margin-right: auto; width: 50%;"/>
	 
2. Trust Certificate

	 Head over to Settings-> General -> Device Management. Tap the developer name and trust the certificate. You will not be able to launch the Uncover jailbreak app on your iPhone/iPad without this.

3. Jailbreak iOS 12.4 using Uncover

	 Open Uncover, tap the Jailbreak button and wait for the app to do its job. Your iPhone or iPad will respring during the process after which you should see the Cydia icon on your home screen.

	 If the app ends up freezing, wait for a few minutes. In case that does not work, reboot your iPhone/iPad and then repeat the above steps.
	
Check out the whole guide [here] (http://www.iphonehacks.com/jailbreak-ios-12).

### How to remove jailbreak on iOS 13.3

Sometimes you have done your testing on jailbroken device and you want to return  your device to how it was. In this case factory reset won't help.

You can easily remove jailbreak from your iOS 13.3 if jailbreaking was done with Cydia and Uncover.

**Steps:**

1. Open Uncover app on your jailbroken iPhone.

2. Tap on Settings gear icon in the top-right corner.

3. Serach for Restore RootFS toggle button and enable it.

4. Return back from settings and tap on Restore RootFS button on Home screen.

	* Note: Maybe removing jailbreak won't work from first try and you will get some error dialogs. If this happens, follow the steps from the error dialog (e.g. Reboot device and try again).

5.  If you encounter any message dialogs just follow the steps from the dialog while removeal of jailbreak is in progress. Also, don't let a device to lock.

6. Wait for the removal of jailbreak to complete.

7. Device will restart and Cydia will no longer be installed on device - jailbreak is now completed.

8. You can now also uninstall the Uncover app.


Reference video: https://youtu.be/bLZ6bTDBGgI

### Testing production builds on iOS

The file that actually gets uploaded to iTunes Connect cannot be installed on a development device since it first has to be signed by Apple. 

This means that "Production" builds on Tryoutapps are not identical to what actually ends up on the App Store, only those that you get via Testflight are. 

That's why you should make sure to always independently verify Testflight builds before they are published to users.

---

![rodney.png](/img/rodney.png)
