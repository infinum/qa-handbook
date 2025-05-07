> *The bitterness of poor quality remains long after the sweetness of meeting the schedule has been forgotten.*

This article will enumerate some tools that might help you test in a particular way or become more productive in your everyday work. Don't think that you have to use all of them all the time. Tools should always help and never get in the way.

## Testing stack

These are some of our dearest tools. 

Some will be briefly mentioned below and others will be covered through other articles of this Handbook.

Use them according to the demands of your particular project.

- **Test case management:** Testrail 
- **Web/mobile cloud testing:** Browserstack 
- **Mobile - UI Automation:** Appium
- **Web - UI Automation:** Selenium
- **API - Functional Testing:** Postman
- **API - Load testing:** k6
- **MITM:** Charles, Proxyman

## Services

### Appbot 
The tool we use for collecting and monitoring user app reviews.

Check it out [here](https://appbot.co/).

### Browserstack Live / App Live
We have a Browserstack license which enables you to test our mobile ("App Live") and web apps ("Live") remotely on real devices. Pretty cool, right?

Check it out [here](https://www.browserstack.com/).

### Browserstack Speedlab

For a quick frontend performance check, you can use the [Browserstack Speedlab](https://www.browserstack.com/speedlab).

### Crashlytics
Crashlytics is a part of Fabric and used for getting crash/error logs from mobile apps.

### Google Analytics
One of the more important analytics tools we use on some projects.

### Google Firebase
Another analytics tool that is so much more. Google started integrating Fabric tools into Firebase after buying the company so you will see Crashlytics there as well.

### Google Dev Console & iTunes Connect
Both are dev dashboards for their respective platforms.

See what they are all about in this [blog post by Vanja](https://infinum.co/the-capsized-eight/google-play-console-vs-itunes-connect-2018).

If you need access, talk to your team lead.

### Invision
A web interface for browsing design files and prototypes.

### Zeplin
A web interface for browsing designs made in Sketch.

## Chrome tools and extensions

### Bug Magnet
[Bug Magnet](https://bugmagnet.org/) is a Google Chrome extension.

Just right-click on any editable item on the page and insert lorems, names, numbers, currencies, payment cards, etc. Check boundaries and edge cases for exploratory testing.

### Chrome Dev Tools
The best thing since sliced bread. Read a short tutorial [in our own Handbook](https://infinum.com/handbook/books/qa/tools/using-chrome-dev-tools).

You can use it to catch errors, measure response times, inspect elements, simulate a mobile device, and much more.

### ChroPath
A Google Chrome extension that will help you locate web elements when doing UI automation.

### Clear Sessions
A Google Chrome extension that will clear all session/cookie data for a particular web page.

### JSONView
A Google Chrome extension that will prettify your JSONs when viewing them in Chrome.

### Markdown Viewer
Helps you view Markdown files in Chrome.

### Screencastify
An extension for easily creating tab screencasts in Google Chrome.

## Android and iOS tools

### Android File Transfer
Used for transferring files between an Android phone and a macOS system. Get it [here](https://www.android.com/filetransfer/).

### Android Debug Bridge (adb)

Used for communicating with your Android device via the terminal.
### Chuck and Loggie

- Chuck is used for inspecting network traffic in Android apps. You can access it from the notifications drawer when the app is running.
- Loggie is a tool made by our own Filip Beć used for inspecting network traffic in iOS apps. Once the app is running and in foreground, you can access it by shaking the phone. :)

Both are useful for inspecting network traffic. If the apps you are testing do not include them, talk to your developers.

### FakeGPS and Lockito (Android)
Tools for mocking your GPS location.

### Google Authenticator
For keeping your 2FA credentials.

### Instruments (iOS)
Tools for inspecting the performance of your app (and much more). Requires XCode.

### Inware and Introspect (Android)
Find all information about your Android device.

### logcat and pidcat (Android)
Both are used for examining Android's device log. Pidcat is just a fancier logcat developed by Saint Jake Wharton.

In order to use it, you will have to install the Android SDK.

You can get pidcat [here](https://github.com/JakeWharton/pidcat). Find more info on using pidcat [in our own Handbook](https://infinum.com/handbook/books/qa/testing/testing-mobile#getting-nice-device-logs).

Use pidcat on debug builds in order to get fetch stack traces and network traffic, among other things.

### Nexus Root Toolkit
Used for changing ROMs on Nexus devices.

### Scrcpy
Use [scrcpy](https://github.com/Genymobile/scrcpy) for easy Android screencasting.

### Shortcuts app (iOS)
For creating and executing scripts on your iOS device.

### Stetho
Stetho is used for examining network traffic, layout, etc. in Android apps via Chrome.

To use it:

- Connect your Android phone to the laptop
 
- Navigate to `chrome://inspect`

- Click the "Inspect" button to begin

You have to ask developers to add it to the app.

### Tunnelbear or UrbanVPN
For connecting to VPNs in various countries. Our account password for Tunnelbear is in 1password. UrbanVPN is free so feel free to sign up (follow [this link](https://www.urban-vpn.com/) for more info about this awesome VPN).

## Other tools

### 1Password
A password manager where we keep credentials for all shared accounts.

### Adobe color wheel
Complementary color [palettes](https://color.adobe.com/create/color-wheel).

### AirDroid
Manage your Android phone/tablet from a web browser without using a cable [here](https://web.airdroid.com/). 

### Alfred
An advanced "Spotlight" for quickly executing certain actions.

### Bash
Command language and shell. See this
[dev.to tutorial](https://dev.to/awwsmm/101-bash-commands-and-tips-for-beginners-to-experts-30je).

### Bensound
Free stock music [here](https://www.bensound.com/).

### Blind text generator
Dummy text generator [here](https://www.blindtextgenerator.com/lorem-ipsum).

### Broken Link Checker
[Dr. Link Check](https://www.drlinkcheck.com/) is a tool that finds links in HTML documents and CSS files. For finding broken and malicious links.

### Canva
Designing photo/video/presentation [editor](https://www.canva.com/).

### Charles
A proxy app used for examining network traffic between your device and a server by staging a man-in-the-middle attack.

### Color picker
Just write "color picker" in Google, and the modal will pop up in the search results. It is used for picking colors and getting color codes.

### Coolors
Create the perfect palette or get inspired by thousands of beautiful [color schemes](https://coolors.co/).

### Copyclip
For accessing your clipboard [history](https://apps.apple.com/us/app/copyclip-clipboard-history/id595191960?mt=12). 

### DaVinci Resolve
Free video [editor](https://www.blackmagicdesign.com/products/davinciresolve/)

### DeviceAtlas
Web usage of a device model by country [here](https://deviceatlas.com/device-data/explorer/webusage/traffic/no-tablet/country/us?search=Apple%20iPhone%20XR).

### Diffchecker
Compare text to find the difference between two text files [here](https://www.diffchecker.com/text-compare/).

### Editing text on the web 
By using the following steps, the text on the web page becomes editable and you can see how it would look if something else was written in the fields:

 	- Right-click and select "Inspect"
 	- Go to "Console"
 	- Write: document.designMode='on'

### File examples
Different file samples (music, videos, pdfs, images,...) [here](https://file-examples.com/).


### Google fonts
Free font [download](https://fonts.google.com/).

### Google Keep / Simplenote
For taking notes.

### IDEs and Text editors
- PyCharm - Python
- Sublime Text
- Visual Studio Code

### IconSVG
Quick [customizable icons](https://iconsvg.xyz/) for your projects.

### I love img 
Every tool you could want to [edit images](https://www.iloveimg.com/) in bulk. 

### Image colour picker
Similar to colour picker, but you can upload your image and find out the cooler used in it [here](https://imagecolorpicker.com/).

### JSONLint
Validator and reformatter for JSON [here](https://jsonlint.com/).

### Jumpcut
Stores all that you have copied or cut in the past, allowing you to quickly find that snippet of text you've been looking for [here](https://snark.github.io/jumpcut/).

### MacDown
For quickly viewing and editing Markdown files.

### OIB generator
OIB (Croatian personal identification number) [generator](https://oib.itcentrala.com/oib-generator/).

### Phrase express
Text expander [software](https://www.phraseexpress.com/), that manages frequently used text templates for insertion into any program.

### Pexel
Free stock photos and videos [here](https://www.pexels.com/).

### PhraseExpress
For pasting templates by entering a simple piece of text.
E.g. enter "bugtemplate" and get an entire bug report template that will replace that entered string so you never have to type out the entire thing again.

### Pixlr
Online [photoshop](https://pixlr.com/). 

### Proxyman
It's like Charles, but a bit more fancy.

### RemoveBG
Remove image background [here](https://www.remove.bg/).

### ResponsivelyApp
For parallel testing on several physical devices.

### Screen to gif
Screen, webcam, and sketchboard recorder with an integrated 
[editor](https://www.screentogif.com/). 

### Send Anywhere
For sending files between mobile and desktop devices.

### Skitch / Monosnap
For taking screenshots.

### Spectacle
For managing your windows.

### Temp mail
Temporary email [generator](https://temp-mail.org/en/).

### Todoist
For managing your own tasks.

### Unsplash
Free stock photos [here](https://unsplash.com/).

### Youtube videos
Download different YT videos or playlists by using [YT-DLP tool](https://github.com/yt-dlp/yt-dlp?tab=readme-ov-file).

This can come in handy when you need to quickly get videos with e.g. specific size, lenght or a format.


## Testing quadrant


For more on tools and testing and to not make this whole article just another dead list, read up on [agile testing quadrants](https://labs.sogeti.com/guiding-development-agile-testing-quadrants/).

![agile-quadrant.png](/img/agile-quadrant.png)


