> Right or wrong, it's very pleasant to break something from time to time. — Fyodor Dostoevsky

## Installing Appium

You just installed Appium (Server or Desktop) and you try to run it but nothing happens. Before you ask Google for help, run `appium-doctor` and make sure the necessary dependencies are ok.

[Appium doctor](https://github.com/appium/appium-doctor)

![troubleshooting_appium_appium_doctor.png](/img/troubleshooting_appium_appium_doctor.png)

Possible fixes:

- Node.js might need an update.
- Make sure you have [Android SDK Platform-Tools package](https://developer.android.com/studio/command-line/adb) installed.
- Make sure to install Xcode and Xcode Command Line Tools.
- Set ANDROID_HOME and JAVA_HOME paths.


NOTE:

Appium Server and Appium Desktop are installed in two different places.

Appium Server: 

`/usr/local/lib/node_modules/appium/node_modules/appium-webdriveragent`

Appium Desktop: 

`/Applications/Appium.app/Contents/Resources/app/node_modules/appium/node_modules/appium-webdriveragent`


## Errors

### Errno 61 Connection refused

```
urllib3.exceptions.MaxRetryError: HTTPConnectionPool(host='localhost', port=4723): 
Max retries exceeded with url: /wd/hub/session (Caused by NewConnectionError('<urllib3.connection.HTTPConnection object at 0x10a4adca0>: 
Failed to establish a new connection: [Errno 61] Connection refused'))
```

It may simply be that you did not start the server. Start the server and the error should be gone. :)


### Could not proxy command

```
selenium.common.exceptions.WebDriverException: 
Message: An unknown server-side error occurred while processing the command. Original error: 
Could not proxy command to the remote server. Original error: socket hang up
```

This error often happens when the device is disconnected. Check the developer options and make sure that the device does not lose the connection because of screen lock, screen saver, etc.

If this error happens while you are using Android, check if the SDK is up-to-date.

After you have checked the developer options and made sure the SDK is up-to-date, try restarting Appium. If the issue persists, try killing the Appium process.

1. Open Terminal
2. Run command: `lsof -Pn -i4`
    - Lists all active processes
3. Run command: `kill -9 <processNumber>` 
    - Kills the specific Appium process, 
    - Or run `killall node` to kill all instances of node.js
4. Start Appium Server again


### Unable to instantiate AppiumDriver

Happens sometimes if you had multiple Appium instances running. Maybe you had both Appium Server and Appium Desktop, or multiple Appium Inspectors running and some processes were not closed properly. Try to kill all those processes and restart Appium.

1. Open Terminal
2. Run command: `killall node`
    - Kills all instances of node.js
3. Start Appium Server again


### Error 65 / Unable to launch the test runner

```
[WebDriverAgent] xcodebuild exited with code '65' and signal 'null'

WebDriverAgentRunner-Runner.app encountered an error (Failed to install or launch the test runner. 
If you believe this error represents a bug, please attach the result bundle at /Users/user/Library/Developer/Xcode/DerivedData/WebDriverAgent-ciegwgvxzxdrqthilmrmczmqvrgu/Logs/Test/Test-WebDriverAgentRunner-2021.12.13_10-50-28-+0100.xcresult. 
(Underlying Error: Unable to launch com.user.WebDriverAgentRunner.xctrunner. 
(Underlying Error: Request to launch com.user.WebDriverAgentRunner.xctrunner failed. The operation couldn’t be completed. 
Unable to launch com.user.WebDriverAgentRunner.xctrunner because it has an invalid code signature, inadequate entitlements or its profile has not been explicitly trusted by the user. : 
Failed to launch process with bundle identifier 'com.user.WebDriverAgentRunner.xctrunner'. 
(Underlying Error: The operation couldn’t be completed. Unable to launch com.user.WebDriverAgentRunner.xctrunner because it has an invalid code signature, inadequate entitlements or its profile has not been explicitly trusted by the user.))))
```

Could happen if:

- The developer is not trusted on the device.
- WebDriverAgentRunner in the Xcode is not set up correctly.
- The Appium version and the iOS version are not compatible.


Fix:

1. Open _WebDriverAgent.xcodeproj_.
2. Select _WebDriverAgentRunner -> `device_serial_number`_ in the toolbar.
3. Select _Product -> Run_ or _Product -> Test_ to install WebDriverAgentRunner to the selected device.
4. Trust the device in the options.

If the issues persist, check that you have correctly set up the Xcode configuration.


### SplashActivity never started

```
Original error: 
'com.infinum.app.ui.splash.SplashActivity' or 'com.infinum.app.repro.mock.com.infinum.app.ui.splash.SplashActivity' never started. 
Visit https://github.com/appium/appium/blob/master/docs/en/writing-running-appium/android/activity-startup.md for troubleshooting

DriverConfigurationError: Could not instantiate new WebDriver instance of type class io.appium.java_client.AppiumDriver 
Unable to create a new remote session. 
Please check the server log for more details. Original error: An unknown server-side error occurred while processing the command. 
Original error: Cannot start the 'com.infinum.app.staging' application. 
```


#### Test execution never starts

If the issue happens on start, you need to add one of the following capabilities:

- `appWaitActivity`

- `appActivity`

For example:

````python
"appium:appActivity": "com.infinum.app.ui.project.ProjectActivity"
````

Read [app activities](https://appium.io/docs/en/writing-running-appium/android/activity-startup/) for more information.

#### Test execution stops during test run

Another reason could be that the app opens a webview, or other screen outside the app, which stays open even after the test is done. When the following test starts, the execution could end with the `SplashActivity` error.

To fix the issue, rearrange the steps in your test and/or add a step that navigates back to the app or closes the screen before the test is done.

For example, step to navigate back to the app:

````python
self.driver.back()
````


### WebDriverAgent keeps getting deleted when opening Appium Inspector

There could be various problems occurring. Some might be related to faulty WebDriverAgent configuration. But it also could be there are still some Appium processes running or that simply there is another Appium Inspector screen already open. That will cause Appium to delete the WDA, which usually only happens on iOS.


### IOException

```
java.io.IOException: Cannot run program "ideviceinstaller": error=2, No such file or directory
```

Fix by installing `ideviceinstaller` manually:

1. Open Terminal
2. Run command: `brew install ideviceinstaller`


## Additional resources

[Troubleshooting Appium](https://appium.io/docs/en/writing-running-appium/other/troubleshooting/)

[Selenium/Appium Troubleshooting](https://developers.perfectomobile.com/pages/viewpage.action?pageId=19170351)
