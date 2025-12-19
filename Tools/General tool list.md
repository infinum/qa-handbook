> *The bitterness of poor quality remains long after the sweetness of meeting the schedule has been forgotten.*

This article will enumerate some tools that might help you test in a particular way or become more productive in your everyday work. Don't think that you have to use all of them all the time. Tools should always help and never get in the way.

## Testing stack

These are some of our dearest tools. 

Some will be briefly mentioned below and others will be covered through other articles of this Handbook.

Use them according to the demands of your particular project.

- **Test case management:** Testrail 
- **Web/mobile cloud testing:** Browserstack 
- **Mobile - UI Automation:** Appium
- **Web - UI Automation:** Playwright
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

### Google Analytics
One of the more important analytics tools we use on some projects.

### Google Firebase
Another analytics tool that is so much more. Google started integrating Fabric tools into Firebase after buying the company so you will see Crashlytics there as well.

### Google Dev Console & iTunes Connect
Both are dev dashboards for their respective platforms.

See what they are all about in this [blog post by Vanja](https://infinum.co/the-capsized-eight/google-play-console-vs-itunes-connect-2018).

If you need access, talk to your team lead.

## Chrome tools and extensions

### Bug Magnet
[Bug Magnet](https://bugmagnet.org/) is a Google Chrome extension.

Just right-click on any editable item on the page and insert lorems, names, numbers, currencies, payment cards, etc. Check boundaries and edge cases for exploratory testing.

### Chrome Dev Tools
The best thing since sliced bread. Read a short tutorial [in our own Handbook](https://infinum.com/handbook/books/qa/tools/using-chrome-dev-tools).

You can use it to catch errors, measure response times, inspect elements, simulate a mobile device, and much more.

### Screencastify
An extension for easily creating tab screencasts in Google Chrome.

## Android and iOS tools

### Android File Transfer
Used for transferring files between an Android phone and a macOS system. Get it [here](https://www.android.com/filetransfer/).

### Android Debug Bridge (adb)
Used for communicating with your Android device via the terminal.

### Google Authenticator
For keeping your 2FA credentials.

### Instruments (iOS)
Tools for inspecting the performance of your app (and much more). Requires XCode.

### Inware and Introspect (Android)
Find all information about your Android device.

### Logcat and pidcat (Android)
Both are used for examining Android's device log. Pidcat is just a fancier logcat developed by Saint Jake Wharton.

In order to use it, you will have to install the Android SDK.

You can get pidcat [here](https://github.com/JakeWharton/pidcat). Find more info on using pidcat [in our own Handbook](https://infinum.com/handbook/books/qa/testing/testing-mobile#getting-nice-device-logs).

Use pidcat on debug builds in order to get fetch stack traces and network traffic, among other things.

### Scrcpy
Use [scrcpy](https://github.com/Genymobile/scrcpy) for easy Android screencasting.

### Tunnelbear or UrbanVPN
For connecting to VPNs in various countries. Our account password for Tunnelbear is in 1password. UrbanVPN is free so feel free to sign up (follow [this link](https://www.urban-vpn.com/) for more info about this awesome VPN).

## Other tools

### 1Password
A password manager where we keep credentials for all shared accounts.

### AirDroid
Manage your Android phone/tablet from a web browser without using a cable [here](https://web.airdroid.com/). 

### Bash
Command language and shell. See this
[dev.to tutorial](https://dev.to/awwsmm/101-bash-commands-and-tips-for-beginners-to-experts-30je).

### Broken Link Checker
[Dr. Link Check](https://www.drlinkcheck.com/) is a tool that finds links in HTML documents and CSS files. For finding broken and malicious links.

### Canva
Designing photo/video/presentation [editor](https://www.canva.com/).

### Charles
A proxy app used for examining network traffic between your device and a server by staging a man-in-the-middle attack.

### Proxyman
It's like Charles, but a bit more fancy.

### Clipy
For accessing your [clipboard history](https://github.com/Clipy/Clipy). 

### Diffchecker
Compare text to find the difference between two text files [here](https://www.diffchecker.com/text-compare/).

### File examples
Different file samples (music, videos, pdfs, images,...) [here](https://file-examples.com/).

### IDEs and Text editors
- PyCharm - Python
- Sublime Text
- Visual Studio Code

### JSONLint
Validator and reformatter for JSON [here](https://jsonlint.com/).

### Pexel
Free stock photos and videos [here](https://www.pexels.com/).

### Pixlr
Online [photoshop](https://pixlr.com/). 

### ResponsivelyApp
For parallel testing on several physical devices.

### Send Anywhere
For sending files between mobile and desktop devices.

### iScreen Shooter
For taking [screenshots / screen recordings](https://apps.apple.com/us/app/iscreen-shoter-screenshot-app/id1596559494?mt=12).

### Youtube videos
Download different YT videos or playlists by using [YT-DLP tool](https://github.com/yt-dlp/yt-dlp?tab=readme-ov-file).

This can come in handy when you need to quickly get videos with e.g. specific size, lenght or a format.

## Testing quadrant

For more on tools and testing and to not make this whole article just another dead list, read up on [agile testing quadrants](https://labs.sogeti.com/guiding-development-agile-testing-quadrants/).

![agile-quadrant.png](/img/agile-quadrant.png)
