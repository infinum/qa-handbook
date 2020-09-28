> *The only system which is truly secure is one which is switched off and unplugged, locked in a titanium lined safe, buried in a concrete bunker, and is surrounded by nerve gas and very highly paid armed guards. Even then, I wouldn’t stake my life on it*

## MobSF
MobSF is a tool for doing a basic automated penetration test on a mobile app.

Here's how to get it up and running:

1. Install [Docker CE Desktop](https://store.docker.com/editions/community/docker-ce-desktop-mac)

2. Start Docker and go through its setup.

3. Check whether Docker is running via its icon in the macOS system dock.

4. Open the terminal and run `docker pull opensecurity/mobile-security-framework-mobsf`. That command will pull the `mobile-security-framework-mobsf` container from DockerHub.

5. Start your web browser and navigate to `localhost:8000` (`0.0.0.0:8000`). If the MobSF app starts, you are good to go.

6. Drag and drop your .IPA or .APK file into MobSF and wait for the pen test to run.

## OWASP ZAP

The OWASP Zed Attack Proxy (ZAP) is another helpfull tool that can help you automatically find security vulnerabilities in web applications while being developed and tested.

Here's how to get it up and running:

1. Download installation file from *[*Github repo*](https://github.com/zaproxy/zaproxy/wiki/Downloads)* 
2. Run the installer 
3. Finish the installation 

For detailed information on how to set up the app use [this handy guide](https://github.com/zaproxy/zaproxy/releases/download/2.7.0/ZAPGettingStartedGuide-2.7.pdf)  

![](/img/OWASP ZAP 2.7.0.png)
OWASP ZAP 2.7.0

## Objection

Objection is a runtime mobile exploration toolkit, powered by [Frida](https://www.frida.re/). 
It was built with the aim of helping assess mobile applications and their security posture without the need for a jailbroken or rooted mobile device.

![](/img/objection.png)

Features 

For all supported platforms, objection allows you to:

1. Patch iOS and Android applications, embedding a Frida gadget that can be used with objection or just Frida itself.
1. Interact with the filesystem, listing entries as well as upload & download files where permitted.
1. Perform various memory related tasks, such as listing loaded modules and their respective exports.
1. Attempt to bypass and simulate jailbroken or rooted environments.
1. Discover loaded classes and list their respective methods.
1. Perform common SSL pinning bypasses.
1. Dynamically dump arguments from methods called as you use the target application.
1. Interact with SQLite databases inline without the need to download the targeted database and use an external tool.
1. Execute custom Frida scripts.

If you want to know more on how to use AppMon please follow this [handy guide](https://github.com/sensepost/objection/wiki/Using-objection). Information on how to patch app via terminal can be found [here](https://github.com/sensepost/objection/wiki/Patching-Android-Applications) 

## AppMon

AppMon is an automated framework for monitoring and tampering system API calls of native macOS, iOS and android apps. It is .useful tool for the mobile penetration testers to validate the security issues report by a source code scanner and by inspecting the APIs in runtime and monitoring the app’s overall activity and focus on things that seem suspicious.It is based on [Frida](https://www.frida.re/).

For more information about setup and how to's please follow this [handy guide.](https://dpnishant.github.io/appmon/)

![](/img/appmon.png)

## QARK
QARK is an easy to use tool capable of finding common security vulnerabilities in Android applications. It features educational information allowing security reviewers to locate precise, in-depth explanations of the vulnerabilities. More you can read more by following this [link](https://engineering.linkedin.com/blog/2015/08/introducing-qark)

Here’s how to get it up and running:

Open terminal and type following command: 

`pip install --user qark` * or *

`pip3 install --user qark`

You will need to install Java on your machine, to do so just follow [this link](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html) 

After finding path to the QARK installation folder use this command to add that path to environment variable:

`sudo nano /etc/paths`


**To launch**

To use QARK with some app you need to download the app package Path to app file that you previously downloaded 

`qark --apk path`

![](/img/QARK apk path .png)

After the decompiling is finished use the generated path to find the report. To do this just copy the path from terminal and paste it to the finder/go/go to folder

![](/img/report path qark.png)

You can send report to the developer along with the decompiled build you can find on your machine under:

`/Users/"your user name"/build`

More information about QARK can be found by following this [link](https://github.com/linkedin/qark).

---

![automated-security-testing.gif](/img/automated-security-testing.gif)
