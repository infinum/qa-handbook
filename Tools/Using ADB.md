> *He who thinks a tool can solve all problems, has a new problem.*

## What is ADB?

Android Debug Bridge (ADB) is a versatile command-line tool that lets you communicate with a device. The ADB command facilitates a variety of device actions, such as installing and debugging apps, and it provides access to a Unix shell that you can use to run a variety of commands on a device. It is a client-server program that includes three components:

**- A client,** which sends commands. The client runs on your development machine. You can invoke a client from a command-line terminal by issuing an adb command.

**- A daemon (adbd),** which runs commands on a device. The daemon runs as a background process on each device.

**- A server,** which manages communication between the client and the daemon. The server runs as a background process on your development machine.

## Install ADB using Homebrew

This is the easiest way and will provide automatic updates:

**1.** Install [Homebrew](https://brew.sh/)

**2.** Open terminal and run: `adb brew cask install android-platform-tools`

**3.** Start using adb: `adb devices`

## How to use ADB

**USB connection**

1. Connect the Android device -> USB cable -> USB dongle -> Mac and activate [“Developer mode”](https://infinum.com/handbook/books/qa/Testing/Testing%20-%20Mobile#enabling-developer-options) on the Android device.

2. Mark the option “Enabling USB Debugging”.

3. Allow USB Debugging to be performed in the security panel.

4. Make sure that the device is successfully connected by running: `adb devices`

**WIFI connection**

1. First of all, connect the Android device via USB cable.

2. Connect Android devices and Mac on the same WIFI network

3. Open terminal and run:

`adb tcpip 5555`

`adb connect 192.168.0.101:5555`

Be sure to replace `192.168.0.101` with the IP address that is actually assigned to your Android device. Now disconnect USB cable and run `adb devices` , your device should be listed as connected.

## ADB basic commands
Print a list of connected devices: `adb devices`

Kill the ADB server: `adb kill-server`

Install an application: `adb install`

Set up port forwarding: `adb forward tcp:6100 tcp:7100`

Copy a file/directory from the device: `adb pull`

Copy a file/directory to the device: `adb push`

Initiate an ADB shell: `adb shell`

## Example of useful testing ADB commands
`adb logcat`
Print the current device log to the console.

`adb logcat -d > [path_to_file]`
Save the logcat output to a file on the local system.

`adb logcat -c` 
The parameter -c will clear the current logs on the device.

`adb logcat packagename:[priority level: V, D, I, W, E, F, S]`
Filter log files by priority e.g. adb logcat com.myapp:E which prints all error logs of the given app.

`adb bugreport > [path_to_file]` 
Will dump the whole device information like dumpstate, dumpsys and logcat output.

`adb shell screencap -p /sdcard/screenshot.png` 
Will create a screenshot of the current screen on the given file location.

`adb shell screenrecord /sdcard/NotAbleToLogin.mp4` 
Will start a recording of the current screen. With CMD+c the current recording can be stopped.

`adb shell cmd package list packages`
This will return a list of the package names of the apps installed on the device.

`adb shell monkey -p com.myAppPackage -v 10000 -s 100`
With the help of this command the monkey tool is generating 10.000 random events on the real device. Note: Use the parameter -s (seed) to execute the same commands over and over again in order to reproduce any crashes that happen during the monkey run.

If you thirst for more knowledge on ADB, check out this [link](https://www.automatetheplanet.com/adb-cheat-sheet/).
