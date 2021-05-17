> *What does a logger say before he cuts down a tree? Let the chimps fall where they may.*

## Automated monkey testing
Monkey testing is a type of testing where you send random inputs to application while checking behavior, or seeing whether the application or system will crash.

Here's how to get it up and running on any Android device:

1. Install [ADB] (https://developer.android.com/studio/command-line/adb?authuser=1) (Android Debug Bridge)

2. Install an application you want to Monkey test on any Android device

3. Connect the Android device with your Mac and click "Trust"

3. Open terminal and run `adb devices` to confirm the device is properly connected (this command should list all connected devices)

4. If you can see the connected device, run `adb shell pm list packages -f > packages.txt` to create "packages.txt" file with all app packages on your Android device.

5. Locate the "packages.txt" file in your home directory and open it

6. Search the name of the application you want to test (e.g. "QA Adventure")

7. If the Facebook" application is installed on your device, you'll probably see something similar to this 
> package:/data/app/co.infinum.qaadventure.staging-1/base.apk=co.infinum.qaadventure.staging

8. Copy the string that starts with the "co", this is the package name we need:
> co.infinum.qaadventure.staging

9. Open terminal again and run `adb shell monkey -p your.package.name -v 5000` or, in my case `adb shell monkey -p co.infinum.qaadventure.staging -v 5000`

10. This will send 5000 random events to the QA Adventure application.

Follow [this link] (https://developer.android.com/studio/test/monkey.html) if you need more information.

---

![dil-monkey.jpg](/img/dil-monkey.jpg)
