> Right or wrong, it’s very pleasant to break something from time to time. — Fyodor Dostoevsky

## Installing Appium

You just installed Appium (Server or Desktop) and you try to run it but nothing happens.
Before you ask Google for help, run `appium-doctor` and make sure the necessary dependencies are ok.

[Appium doctor](https://github.com/appium/appium-doctor)

![troubleshooting_appium_appium_doctor.png](/img/troubleshooting_appium_appium_doctor.png)

Common fixes:

- Node.js might need an update
- Make sure you have [Android SDK Platform-Tools package](https://developer.android.com/studio/command-line/adb) installed
- Make sure to install XCode and XCode Command Line Tools
- Set ANDROID_HOME and JAVA_HOME paths


NOTE:

Appium Server and Appium Desktop are installed in two different places.

Appium server

`/usr/local/lib/node_modules/appium/node_modules/appium-webdriveragent`

Appium Desktop

`/Applications/Appium.app/Contents/Resources/app/node_modules/appium/node_modules/appium-webdriveragent`


## Running tests

Appium runs tests alphabetically. It will first go through test files by name in alphabetical order.
Then it will again go alphabetically through the tests inside each test file / class.

One way to override that is to name your tests prefixed with numbers, something like:
    - test_001 (or test_001_001)
    - test_001_002 
    - ...

If your tests are independent of each other, then you might not have to worry about the test order. In some cases, you might need to link a few tests and in that case you will have to keep this in mind.


## Errors

### Errno 61 Connection refused

`urllib3.exceptions.MaxRetryError: HTTPConnectionPool(host='localhost', port=4723): Max retries exceeded with url: /wd/hub/session (Caused by NewConnectionError('<urllib3.connection.HTTPConnection object at 0x10a4adca0>: Failed to establish a new connection: [Errno 61] Connection refused'))`

Sounds a bit scary, but it might simply be that you did not start the server at all.
Start the server and the error should be gone :)


### Could not proxy command

`selenium.common.exceptions.WebDriverException: Message: An unknown server-side error occurred while processing the command. Original error: Could not proxy command to the remote server. Original error: socket hang up`

This error often happens when the device is disconnected. Check the developer options and make sure that the device does not lose the connection because of screen lock, screen saver, etc.

If this error happens while you are using Android, check if the SDK is up-to-date.

After you have checked the developers options and made sure the SDK is up-to-date, try restarting Appium.
If the issue stills persists, try killing the appium process.

1. Open Terminal

2. Run command `lsof -Pn -i4` to see all active processes

3. Run command `kill -9 <processNumber>` to kill the specific process, or simply `killall node` to kill all instances of node.js

4. Start Appium server again


### Unable to instantiate AppiumDriver

Happens sometimes if you had multiple Appium instances running. Maybe you had both Appium Server and Appium Desktop, or multiple Appium Inspectors running and some process were not closed properly.
Try to kill all those processes and restart Appium.

1. Open Terminal

2. Run command `killall node` to kill all instances of node.js

3. Start Appium server again


### Error 65

`[WebDriverAgent] xcodebuild exited with code '65' and signal 'null'`

`WebDriverAgentRunner-Runner.app encountered an error (Failed to install or launch the test runner. If you believe this error represents a bug, please attach the result bundle at /Users/user/Library/Developer/Xcode/DerivedData/WebDriverAgent-ciegwgvxzxdrqthilmrmczmqvrgu/Logs/Test/Test-WebDriverAgentRunner-2021.12.13_10-50-28-+0100.xcresult. (Underlying Error: Unable to launch com.user.WebDriverAgentRunner.xctrunner. (Underlying Error: Request to launch com.user.WebDriverAgentRunner.xctrunner failed. The operation couldn’t be completed. Unable to launch com.user.WebDriverAgentRunner.xctrunner because it has an invalid code signature, inadequate entitlements or its profile has not been explicitly trusted by the user. : Failed to launch process with bundle identifier 'com.user.WebDriverAgentRunner.xctrunner'. (Underlying Error: The operation couldn’t be completed. Unable to launch com.user.WebDriverAgentRunner.xctrunner because it has an invalid code signature, inadequate entitlements or its profile has not been explicitly trusted by the user.))))`

Could happen if:

- developer has not been trusted on the device
- WebDriverAgentRunner in the XCode has not been set up correctly
- the Appium version and the iOS version are not compatible


Fix:

1. Open WebDriverAgent.xcodeproj

2. Select _WebDriverAgentRunner > `device_serial_number`_ in the toolbar

3. Select _Product > Run_ or _Product > Test_ to install WebDriverAgentRunner onto the selected device 

4. Trust the device in the options

If the issues persists, check that you have correctly set up the Xcode configuration.


### SplashActivity' never started

`Original error: 'com.signify.masterconnect.ui.splash.SplashActivity' or 'com.signify.masterconnect.repro.mock.com.signify.masterconnect.ui.splash.SplashActivity' never started. Visit https://github.com/appium/appium/blob/master/docs/en/writing-running-appium/android/activity-startup.md for troubleshooting`

Could be any number of things. Check Appium logs for more details.

One of the issues is when an app opens a webview which stays open even after the tests is done.
If the webview stays open when the following test starts, the execution will end in the error.


### WebDriverAgent keeps getting deleted when opening Appium Inspector

There could be various problems occurring. Some might be related to faulty WebDriverAgent configuration.
But it also could be there are still some Appium processes running or that simply there is another inspector screen already running.
That will cause Appium to delete the WDA, usually only happens on iOS.


### IOException

`java.io.IOException: Cannot run program "ideviceinstaller": error=2, No such file or directory`

Fix by installing `ideviceinstaller` manually.

1. Open Terminal

2. Run command `brew install ideviceinstaller`


## Additional resources

[Troubleshooting Appium](https://appium.io/docs/en/writing-running-appium/other/troubleshooting/)

[Selenium/Appium Troubleshooting](https://developers.perfectomobile.com/pages/viewpage.action?pageId=19170351)


---


![dilbert_troubleshooting_appium.png](/img/dilbert_troubleshooting_appium.png)
