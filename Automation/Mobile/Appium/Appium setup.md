> *Automation does not do what testers used to do, unless one ignores most things a tester really does. Automated testing is useful for extending the reach of the testers work, not to replace it.*

### General prerequisites

Before installing [Appium](https://appium.io/), ensure the core dependencies and required development tools are installed and configured. In general you will need:

* [Homebrew](https://brew.sh/)
* [Java](https://www.java.com/en/)
* [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
* [node.js](https://nodejs.org/en/) 

### Platform specific prerequisites

#### iOS / macOS

* one of the latest [Xcode](https://developer.apple.com/support/xcode/) versions
  * Xcode update might require you to update your macOS as well
* [Xcode command line tools](https://www.freecodecamp.org/news/install-xcode-command-line-tools/)


#### Android

* [Android Studio](https://developer.android.com/studio/)
* Android SDK tools

The easiest way to install Android SDK tools is through Android Studio:

1. Open _Settings_
2. Search for _Android SDK_
3. Open the _SDK Platforms_ tab 
4. Select the checkbox next to the API version(s) you want to install 
5. Open the _SDK Tools_ tab 
6. Select the _Android SDK Platform-Tools_ checkbox
7. Select the _Android SDK Build-Tools_ checkbox
8. Click _Apply_ and wait for the packages to install

![android_studio_sdk.png](/img/android_studio_sdk.png)

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


Make sure to check [Appium requirements](https://appium.io/docs/en/latest/quickstart/requirements/) before installing.

Appium team provides support only for the most recent version of Appium. Reffer to Appium [migration](https://appium.io/docs/en/latest/guides/migrating-2-to-3/) docs if you wish to upgrade from an older major Appium version.
 
To install latest Appium version simply run:

* `npm install -g appium`

#### Appium drivers

However, Appium does not include drivers by default and you need to install them using Appium. They have to be installed separately for each platform on which you intend to run the tests. You can learn more about Appium drivers ecosystem [here](https://appium.io/docs/en/latest/ecosystem/drivers/).

iOS driver: 

* `appium driver install xcuitest`

Android driver:

* `appium driver install uiautomator2`

#### Appium-related tools

[Appium Doctor](https://appium.io/docs/en/2.4/ecosystem/tools/#appium-doctor) CLI tool can be used to validate proper environment setup for Android and iOS automation. You can install it by:

* `npm install -g @appium/doctor`

To check if dependencies are installed correctly run:

* `appium-doctor`

The necessary dependencies should have a green check mark:

![troubleshooting_appium_appium_doctor.png](/img/troubleshooting_appium_appium_doctor.png)


#### Capabilities

[Capabilities](https://appium.io/docs/en/latest/guides/caps/) are parameters that you need to define to start an Appium session. They have to be defined as key-value pairs.

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

**NOTE:**

* Some capabilities should not be combined since they might interfere with each other. See [Reset Strategies](https://appium.readthedocs.io/en/stable/en/writing-running-appium/other/reset-strategies/) for more details.

* If you use `autoAcceptAlerts` (iOS only), it could happen that some of the native app dialogs get accepted / declined when you don't expect it. You might want to avoid this capability and handle the dialogs within the test.

* If using `useNewWDA`, it might not work as expected due to Apple restrictions.

  * Set it to true if you want to apply different startup options for WebDriverAgent for each session.

  * It should be stable on Simulator. However, it gets tricky with real devices. 
  
  * For real devices it is better to have WebDriverAgent client installed manually, without having it reinstalled during each session.
