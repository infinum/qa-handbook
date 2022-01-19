## Android - Profiler

This tool helps you find where your app uses more energy than necessary.  
It consists of three timelines: Event timeline, Energy timeline and System timeline.  
The Profiler monitors the use of CPU, network, GPS and system events and presents them in form of bars and horizontal lines (system events).  
The higher/longer the bar is, the more energy is being used.  
You can place a mouse over any part of the timeline for more info.

 ![1_battery.png](/img/1_battery.png)


## Prerequisites:

### Enabled developer options

1. Go to Software info (location varies depending on phone brand) 
2. Tap multiple times on "Build Number" (or "MIUI version" for Xiaomi devices) until you see a toast 	message: "You are "X" steps away from being a developer."  
3. Enable "Developer options" (location varies depending on phone brand)

### Enabled USB Debugging + Debug build

1. USB debugging (found under "Developer options") set to "ON".
2. "Allow USB debugging" prompt set to "OK" and "Always allow from this computer" checked (this prompt shows up when the phone is connected to a computer for the first time).
3. Installed _debug_ build of the app you plan to monitor (kindly ask your developer to make one for you). In case your device is rooted, you can monitor any build.	

## Steps:

1. [Download](https://developer.android.com/studio), install and run Android Studio.
2. Click on "New Project".
3. Select "No Activity" and click Next.
4. Set the "Name" and "Android version" that isn't above the one you are running on your test device (otherwise Android Studio will notify you with a warning).
5. Your device should be visible in the top bar, next to the green "Play" button (if it isn’t, check the troubleshooting section of this article).
6. Click on "Profiler" in the bottom bar of Android Studio.  
 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:100%;">![2_battery.png](/img/2_battery.png)</span>  
7. Click on "+". Your test device should be present here.  
 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:100%;">![3_battery.png](/img/3_battery.png)</span>   
8. Select the device and the app you want to monitor.
In case your app isn't present, try to run it on your device first to trigger a refresh in Android Studio.
9. Once the session starts, the only thing left is to click on the "Energy" timeline to zoom on battery consumption. The monitoring lasts until you press the "Stop" button. After stopping, you can inspect the recorded session.

 ![4_battery.png](/img/4_battery.png)

 ![5_battery.png](/img/5_battery.png)
  

The Energy Profiler provides the user with insight into the usage of these events and processes to check if there are any excessive impacts on the battery.  
For more info about "wake locks", "alarms" and "jobs" check [this](https://developer.android.com/studio/profile/energy-profiler#inspect_system_events_wake_locks_jobs_and_alarms).

 

## Troubleshooting - what to do if it doesn't work 

1. Check if you have ADB installed on your computer (if your are not sure or ask yourself "What is ADB?" check [this](https://infinum.com/handbook/books/qa/tools/using-adb)).
2. Check if you set "USB debugging" to "ON".  
3. Try the "Revoke USB debugging authorizations" option, disconnect the phone, connect it again and allow the connection via the prompt that shows up.
4. Try other USB cables.  
It is not so uncommon to connect the phone to a computer by micro USB cable, only to find out that the cable you used can only charge the device ([more info](https://www.dignited.com/50330/usb-data-cable-vs-usb-charging-cable/)).  
USB-C cables are a bit better in that aspect but even they [aren't all the same](https://cdn-learn.adafruit.com/assets/assets/000/085/324/medium800/components_adafruit_USB_C_graphic_outlines.png?1575491911). 
5. Make sure that the app you plan to monitor is a debug build.
6. In case you don't see the app you want to monitor in Android Studio - try to run it on the device first, that should trigger a refresh in Android Studio. 

## Running Android Profiler without Android Studio

There is an [option](https://developer.android.com/studio/profile/android-profiler#standalone-profilers) to run Android Profiler without running full Android Studio.  
The only requirement is Java installed on the computer you are using and that the Profiler isn’t currently running inside Android Studio.
