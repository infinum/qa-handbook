> *Automation does not do what testers used to do, unless one ignores most things a tester really does. Automated testing is useful for extending the reach of the testers work, not to replace it.*

### General setup

Before you start with [Appium](https://appium.io/) installation, there are a few other steps you need to do and tools to install.

Install:

* [Java](https://www.java.com/en/)
* [Android Studio](https://developer.android.com/studio/)
* [Homebrew](https://brew.sh/)
* [Xcode](https://developer.apple.com/support/xcode/)
* [npm](https://docs.npmjs.com/)
* [node.js](https://nodejs.org/en/)

See [Appium requirements](https://github.com/appium/appium#requirements) for more details.

#### Environment variables

Set JAVA_HOME and ANDROID_HOME environment variables.

1. Open the profile file:
   - zsh: `open ~/.zshrc`
   - bash: `open ~/.bashrc`
2. Type in the following:

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

Appium 1.x is no longer maintained. Make sure to run [Appium 2.x](https://github.com/appium/appium).

Appium 2.x does not include drivers by default. They have to be installed separately for each platform on which you intend to run the tests.

1. Install Appium
    - `npm install -g appium@next`
2. Install Appium Doctor
   - `npm install -g @appium/doctor`
3. Install xcuitest (iOS) driver
   - `appium driver install xcuitest`
4. Install uiautomator2 (Android) driver
   - `appium driver install uiautomator2`
5. Check dependencies are installed correctly
   - `appium-doctor`
   - The necessary dependencies should have a green check mark

See [Appium Pro post](https://appiumpro.com/editions/122-installing-appium-20-and-the-driver-and-plugins-cli) for more details.


#### Desired capabilities (options) explained

```
capabilities = {
   "appium:platformName": "iOS",
   "appium:platformVersion": platform_version,
   "appium:udid": device_udid,
   "appium:app": app_path,
   "appium:deviceName": "iPhone",
   "appium:xcodeOrgId": your_personal_xcodeOrgId,
   "appium:xcodeSigningId": "iPhone Developer",
   "appium:automationName": "XCUITest",
   "appium:useNewWDA": False,
   "appium:autoAcceptAlerts": True,
   "appium:noReset": True
}
```


| Capability       | Purpose                                                                                                                                                                                                                                                                                                                                                      | Example                                   |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------|
| platformName     | Which mobile platform to use                                                                                                                                                                                                                                                                                                                                 | "Android", "iOS"                          |
| platformVersion  | Mobile OS version                                                                                                                                                                                                                                                                                                                                            | Just the major version, e.g. "13"         |
| udid             | Unique device identifier (serial number) of the connected physical device                                                                                                                                                                                                                                                                                    | "1R2TV3BD"                                |
| app              | The absolute local path or remote HTTP URL to an .ipa (iOS) or .apk (Android) file                                                                                                                                                                                                                                                                           ||
| deviceName       | The kind of mobile device you're using                                                                                                                                                                                                                                                                                                                       | Device name for Android, "iPhone" for iOS |
| xcodeOrgId       | A unique 10-character string generated by Apple that is assigned to you or your team.                                                                                                                                                                                                                                                                        | "A1B5C3D5E2"                              |
| xcodeSigningId   | This capability is required if you want to test on real device. There's no need to change it's value.                                                                                                                                                                                                                                                        | "iPhone Developer"                        |
| automationName   | Which automation engine to use                                                                                                                                                                                                                                                                                                                               | "XCUITest" or "UIAutomator2"              |
| useNewWDA        | If true, forces uninstall of any existing WebDriverAgent app on device. Set it to true if you want to apply different startup options for WebDriverAgent for each session. Although, it is only guaranteed to work stable on Simulator. Real devices require WebDriverAgent client to run for as long as possible without reinstall/restart to avoid issues. | "False"                                   |
| autoAcceptAlerts | Accept all iOS (only!) alerts automatically if they pop up. This includes privacy access permission alerts (e.g., location, contacts, photos). Default is false.                                                                                                                                                                                             | "True"                                    |
| noReset          | Don't reset app state before this session. See [Reset Strategies](http://appium.io/docs/en/writing-running-appium/other/reset-strategies/index.html) for more details.                                                                                                                                                                                       | "True"                                    |

See [Appium Desired Capabilities](https://appium.io/docs/en/writing-running-appium/caps/#appium-desired-capabilities) for more details.