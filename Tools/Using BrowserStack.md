Testing a web application on every browser and platform is not a simple task. There is a tool that you can use to make this process easier. BrowserStack might solve your application testing problem.

## What is BrowserStack?

BrowserStack is a cloud web and mobile testing platform that provides the ability to test websites and mobile applications across on-demand browsers, operating systems, and real mobile devices.

BrowserStack consists of four primary products:

1. Live
2. App live
3. Automate
4. App Automate

BrowserStack can be accessed on its [login page](https://www.browserstack.com/users/sign_in) using credentials found in 1Password. Please, do **NOT** change the login credentials and do **NOT** enable SSO without consulting with QA Team Lead(s).


## What is cross-browser testing?

Cross-browser tests are functional tests. These tests are performed to check whether an application works as expected in different web browsers and operating systems. We can run test cases manually or automated by specifying different browsers in automation scripts.

## BrowserStack's main advantages

- Cross-browser testing with different browsers on different operating systems.
- Native app testing on real mobile devices.
- Hybrid application testing.
- Option to run automated test for web and mobile apps.


## Testing a web app using desktop browsers

1. Log in.
 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:70%;">![login.png](/img/login.png)</span>
2. Choose the "Live" (Interactive cross-browser testing) option from the Products dropdown.
 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:70%;">![products.png](/img/products.png)</span>
3. Choose an OS (Windows or Mac) from the list (on the left side). You will then see a list of browsers with different versions.
 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:70%;">![browser-list.png](/img/browser-list.png)</span>
4. Choose a browser version that you want to test on.
 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:70%;">![loading.png](/img/loading.png)</span> 
5. Once the browser opens, enter the URL of the web application you want to test. You can test the app the same way as you would do in real system browsers.
 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:70%;">![web-testing.png](/img/web-testing.png)</span>

### Live options

- **Switch Browser** - if you want to choose a different browser, click on the "Switch Browser" option (this will take you to the Dashboard screen where you can select another browser). 
- **Resolution** - if you want to test the application on a different resolution, click the "Resolution" icon and a list of available resolutions will appear. 
- **Local Testing** - to resolve all requests to local URLs via your machine, click on the "Local Testing" icon and check "Resolve all URLs through my network" option. Local Testing gives you the option to test websites hosted on your private network. 
- **Report a bug** - it gives you the option to highlight a bug, and send the bug report along with a screenshot (via Jira, Trello, GitHub, Slack, or email) or if you can download the screenshot
- **Stop Session** - when you finish testing in a specific browser, click "Stop Session" to return to the Dashboard.


## Testing a web app using mobile browsers

1. Choose the "Live" (Interactive cross-browser testing) option from the Products dropdown.
 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:70%;">![products.png](/img/products.png)</span>
2. Choose an OS (Android or iOS) from the list (on the left side). You will then see a list of avialable devices.
 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:70%;">![mobile-browser-list.png](/img/mobile-browser-list.png)</span>
3. Hover over the device you want to test on and you will see the supported browsers (like Chrome, Mozilla Firefox, Safari, UC browser, etc.)
4. Select a browser. The selected browser will open.


## Testing a native mobile application on real devices

1. Choose the "App Live" (Interactive native & hybrid app testing) option from the Products dropdown. 
 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:70%;">![products.png](/img/products.png)</span>
2. You will see 3 main options there (to choose/upload the app, a list of Android devices, and a list of iOS devices).
 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:70%;">![live-app.png](/img/live-app.png)</span>
3. Click on the "Upload" button and a system dialog box will open.
4. Select the app file you want to upload. The uploaded app will be visible under the "Uploaded Apps" section. (Note: the app upload limit size is 1 GB).
5. Once the app is uploaded, select the app file along with the device you want to test on. 
The session will start and the app will be installed on the chosen device. 

There are also some alternative ways to install the app:

- installing via Play Store, App Store or TestFlight
- sync with App Center

**Installing an app via Play Store:**

1. Open the "Sources" list
2. Choose "Install via Play Store"
3. Select an Android device from the "Android Real Devices" tab. The session will start and Play Store will open on the device.
4. Sign in to your account and find the app you want to test. 
5. Download and install the app. 


### App Live options

- **Switch Device** - if you want to choose a different device, click on the "Switch Device" option.
- **Local Testing** - to resolve all requests to local URLs via your machine, click on the "Local Testing" icon and check "Resolve all URLs through my network" option.
- **Stop Session** - when you finish testing in a specific device, click "Stop Session" to return to the Dashboard. 
- **Rotate Device** - use this option to rotate the device horizontally or vertically. 
- **Install New App** - install a new application to the selected device. 
- **Kill/Uninstall** - option to close or uninstall the app on the device. 
- **Change Location** or **Language** - you change the location and language data. 
- **Device Info** - you can find complete device information there.

<span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:70%;">![live-app-load.png](/img/live-app-load.png)</span>

## Comparison of BrowserStack testing over real device testing

**BrowserStack testing** is cheap. We can test web and mobile applications on numerous devices and browsers. It gives us a wide range of possibilites and flexibility as it offers cross-browser testing and mobile application testing on real devices and multiple OS version. There is no need to buy an OS license. 
A drawback is that it can sometimes be slow because you need to wait for all the data to be loaded (like OS, browsers, app installs, etc.). 

**Real device testing** is not very cheap. You need to buy the devices that you need for testing. Also, it is not very practical to carry all those devices with you. Additionally, you need to buy an OS license.

