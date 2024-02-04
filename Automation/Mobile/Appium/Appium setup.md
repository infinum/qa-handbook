> *Automation does not do what testers used to do, unless one ignores most things a tester really does. Automated testing is useful for extending the reach of the testers work, not to replace it.*

### General setup

Before you start with [Appium](https://appium.io/) installation, there are a few more tools to install, and steps to take.

Make sure you have installed:

* one of the latest [Xcode](https://developer.apple.com/support/xcode/) versions
  * Xcode update might require you to update your macOS as well
* [Xcode command line tools](https://www.freecodecamp.org/news/install-xcode-command-line-tools/)


To use Appium, you also need to install:

* [Homebrew](https://brew.sh/)
* [Java](https://www.java.com/en/)
* [Android Studio](https://developer.android.com/studio/)
* [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
* [node.js](https://nodejs.org/en/)

See [Appium requirements](https://github.com/appium/appium#requirements) for more details.


#### Android SDK tools

The easiest way to install Android SDK tools is through Android Studio.

1. Open _Settings_
2. Open _Appearance & Behavior_ > _System Settings_ > _Android SDK_
3. Open the _SDK Platforms_ tab 
4. Select the checkbox next to the API version(s) you want to install 
5. Open the _SDK Tools_ tab 
6. Select the _Android SDK Platform-Tools_ checkbox
7. Select the _Android SDK Build-Tools_ checkbox
8. Click _Apply_ and wait for the packages to install


![android_studio_sdk.png](..%2F..%2F..%2Fimg%2Fandroid_studio_sdk.png)

#### Environment variables

Set _JAVA_HOME_ and _ANDROID_HOME_ environment variables.

1. Open the profile file:
   - zsh: `open ~/.zshrc`
   - bash: `open ~/.bashrc`
2. Type in the following (make sure to use your username and versions):

```
export ANDROID_HOME=/Users/<username>/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/platform-tools/
export PATH=$PATH:$ANDROID_HOME/build-tools/<version>
export PATH=$PATH:$ANDROID_HOME/tools/bin

export JAVA_HOME=`/usr/libexec/java_home`
export PATH=${JAVA_HOME}/bin:$PATH
export PATH=${PATH}:${JAVA_HOME}
```


### Install Appium

Appium 1.x is no longer being maintained. Make sure you use [Appium 2.x](https://github.com/appium/appium).

Appium 2.x does not include drivers by default. They have to be installed separately for each platform on which you intend to run the tests.
See [Installing Appium 2.0](https://appiumpro.com/editions/122-installing-appium-20-and-the-driver-and-plugins-cli) for more details.


1. Install Appium
    - `npm install -g appium`
2. Install [Appium Doctor](https://appium.io/docs/en/2.4/ecosystem/tools/#appium-doctor)
   - `npm install -g @appium/doctor`
3. Install xcuitest (iOS) driver
   - `appium driver install xcuitest`
4. Install uiautomator2 (Android) driver
   - `appium driver install uiautomator2`
5. Check dependencies are installed correctly
   - Run the `appium-doctor` command in the terminal
   - The necessary dependencies should have a green check mark

![troubleshooting_appium_appium_doctor.png](..%2F..%2F..%2Fimg%2Ftroubleshooting_appium_appium_doctor.png)


#### Capabilities

Capabilities are parameters that you need to define to start an Appium session. They have to be defined as key-value pairs.

Some are mandatory, such as `platformName` and `udid`. Most are optional but can be very useful in your project. For example, accepting all permissions by default without having to do it in your tests.

Example:

```
capabilities = {
   "appium:app": "project/builds/b1.103.ipa",
   "appium:automationName": "XCUITest",
   "appium:platformName": "iOS",
   "appium:platformVersion": 17,
   "appium:udid": 1R2TV3BD,
   "appium:deviceName": "iPhone",
   "appium:xcodeOrgId": "A1B5C3D5E2",
   "appium:xcodeSigningId": "iPhone Developer",
   "appium:useNewWDA": False,
   "appium:usePreinstalledWDA": True,
   "appium:updatedWDABundleId": "com.appiumApp.WebDriverAgentRunner",
   "appium:autoAcceptAlerts": True,
   "appium:noReset": True,
}
```


| Capability             | Description                                                                                                                                               | Example            |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------|
| platformName           | The mobile platform which is used                                                                                                                         | "Android"          |
| platformVersion        | Mobile OS version (major version only)                                                                                                                    | "13"               |
| udid                   | Unique device identifier (serial number) of the connected physical device                                                                                 | "1R2TV3BD"         |
| app                    | The absolute local path or remote HTTP URL to an .ipa (iOS) or .apk (Android) file                                                                        | <path_to_file>     |
| deviceName             | The mobile device name (only useful for iOS simulators; it is recommended to specify the device using the `udid` capability)                              | "iPhone 12"        |
| xcodeOrgId             | A unique 10-character string generated by Apple that is assigned to you or your team                                                                      | "A1B5C3D5E2"       |
| xcodeSigningId         | Capability required for testing on real device. Should be set to `iPhone Developer`                                                                       | "iPhone Developer" |
| automationName         | Name of the automation driver                                                                                                                             | "UIAutomator2"     |
| useNewWDA              | If true, uninstalls existing WebDriverAgent app from the device                                                                                           | "False"            |
| autoAcceptAlerts       | Accepts all (_iOS only_) alerts automatically if they pop up. This includes privacy access permission alerts (e.g., location, contacts). Default is false | "True"             |
| autoGrantPermissions   | Accepts all (_Android only_) permissions. This includes privacy access permission alerts (e.g., location, contacts). Default is false                     | "True"             |
| noReset                | If true, the app state is not reset during the session                                                                                                    | "True"             |


**NOTE:**
- Some capabilities should be combined since they might interfere with each other.
  - See [Reset Strategies](https://appium.readthedocs.io/en/stable/en/writing-running-appium/other/reset-strategies/) for more details.
- If you use `autoAcceptAlerts` (iOS only), it could happen that some of the native app dialogs get accepted / declined when you don't expect it.
  - You might want to avoid this capability and handle the dialogs within the test.
- If using `useNewWDA`, it might not work as expected due to Apple restrictions.
  - Set it to true if you want to apply different startup options for WebDriverAgent for each session.
  - It should be stable on Simulator. However, it gets tricky with real devices. 
  - For real devices it is better to have WebDriverAgent client installed manually, without having it reinstalled during each session.
