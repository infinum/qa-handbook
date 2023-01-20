> *Automation does not do what testers used to do, unless one ignores most things a tester really does. Automated testing is useful for extending the reach of the testers work, not to replace it.*

Unlike Android, the iOS ecosystem is a bit more cocooned. That means that the setup requires a few additional steps when compared to the Android setup.

You can set up the iOS configuration in two ways:

* Automatically

	* By running the iOS test, the application under test (or so called WebDriverAgentDriver) is signed automatically. This is possible to achieve by setting the correct signing certificate and provisioning profile to a "dummy project" and turning on the "Sign automatically" feature. More on that bellow.
* Manually

	* More often than not, life doesn't turn out the way we want it to. Meaning, automatic configuration could fail for different reasons. If that's how your beans fell, we got you covered with the <a href="#manual-configuration">Manual configuration</a>.


#### Where to find the app's [bundle ID](https://developer.apple.com/documentation/appstoreconnectapi/bundle_ids)

1. Download the `.ipa` file
2. Change the extension of the `.ipa` file to `.zip`
3. Unzip the file and open the _Payload_ folder
4. Right-click on the file and select the _Show package contents_ option
5. Open the `.plist` file to find the _Bundle identifier_


#### Automatic configuration

1. Open Xcode
2. Click **Create a new Xcode project**
3. Choose the Application template (e.g. **Single View App**) and click **Next**
4. Enter product name
   - E.g. _Demo application_
5. Click **Add account** and use **your personal** iCloud account
6. Click **Team** dropdown and choose **your personal** account
7. Make sure the _Automatically manage signing_ option is checked
8. Enter Organization Identifier and click **Next**
   - E.g. _com.appiumtest.demo-application_
9. Choose the Project location and click **Done**
10. Close the Xcode project
11. Open terminal and run `brew install libimobiledevice --HEAD`. 
    - In case of **Permission denied** error, check step 6 from the <a href="#manual-configuration">Manual configuration</a> setup.
12. Connect your physical iPhone to your Mac
    - Make sure it's trusted device
13. Enter `idevice_id --list` in the terminal and hit enter
14. Copy the ID and use it as a **UDID/device name**
15. Start Appium Server
16. Open your Appium project in PyCharm
17. Make sure there's an `.ipa` file in the project's _builds_ folder
18. Run the tests

There's a huge chance an error pops up, most likely:

```
No profiles for 'com.facebook.WebDriverAgentRunner.xctrunner were found: 
Xcode couldn't find any iOS app Development provisioning profiles matching com.facebook.WebDriverAgentRunner.xctrunner'.
```

In that case, do the following:

1. Inspect the Appium server logs and find the WebDriverAgent path the XCUITest driver is using
   - Most probably `/usr/local/lib/node_modules/appium/node_modules/appium-xcuitest-driver/node_modules/appium-webdriveragent/` 
2. Open the `WebDriverAgent.xcodeproj` from the folder (using Xcode)
3. Click the _WebDriverAgent_ from the Project navigator
4. Open **Signing & Capabilities** tab
5. Choose _WebDriverAgentLib_ from the **Targets** section
6. Manually choose **your personal account** under _Team_ 
   - Wait for the signing process to finish
7. Next, choose _WebDriverAgentRunner_ from the **Targets** section
8. Again, manually choose **your personal account** under _Team_ 
   - Wait for the signing process to finish
   - The signing will probably fail due to the wrong Bundle identifier. Don't worry, we'll fix that
9. Click the **Build Settings** tab
10. Find the **Packaging** category and double-click the **Product Bundle Identifier**. 
11. Change the value to something unique like _com.your_name.WebDriverAgentRunner_ and try to sign it again
12. Save the project and run the Appium project

	
#### Manual configuration

1. [Download](https://appium.io/) the Appium client (by pressing the **Download Appium** button)
2. Move the application to the **Application folder** 
3. Install [Homebrew](https://brew.sh/)
4. Install [Node.js](https://nodejs.org/en/)
5. Using terminal, run `npm install -g appium`
	* The error *Permission denied* could potentially appear. In that case:
      * Run `sudo chmod 777 /usr/local/lib/node_modules` and type your password
      * Enter `npm install -g appium` again

6. Run `brew install libimobiledevice --HEAD` 
	* If *Permission denied* error appears, run:
      - `sudo chmod 777 /usr/local/share/doc`
      - `sudo chmod 777 /usr/local/share/man`
      - `sudo chmod 777 /usr/local/share/man/man1`
      - `brew install libimobiledevice --HEAD`

7. Run `brew install carthage`
8. Install the latest Xcode to continue with the setup
	* The important step is to open Xcode application and accept the Agreement, download the latest updates and open it for the first time
9. Run `npm install -g ios-deploy --unsafe-perm=true`
	* You’ll probably see some *xcodebuild requires Xcode* error. In that case, run: 
      * `sudo xcode-select --switch /Library/Developer/CommandLineTools`
    * After entering the password, run the `npm install -g ios-deploy --unsafe-perm=true` command again. 
      * If the issue persists, run:
        * `rm -rf ~/Library/Developer/Xcode/DerivedData/* `
        * `npm -g uninstall ios-deploy`
        * `npm -g install ios-deploy@beta`
