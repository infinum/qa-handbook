# Android - Profiler

This tool helps you find where your app uses more energy than necessary.  
It consists of three timelines: Event timeline, Energy timeline and System timeline.  
Profiler monitors use of CPU, network, GPS and system events and presents them in form of bars and horizontal lines (system events).  
Higher/longer the bar is - more energy demanding that part is.  
You can place mouse over any part of timeline for more info.

 ![1_battery.png](/img/1_battery.png)


## Prerequisites:
###Developer options
1.  Go to Software info (Location varies depending on phone brand), 
2.  Tap multiple 	times on "Build Number" (or "MIUI version") till you see toast 	message: "You are "X" steps away from being a developer."  
3. Enable "Developer options"  
Xiaomi/Realme - Settings, Additional settings  
Huawei/Samsung - Settings  
LG - System

###USB Debugging + Debug build
4. ADB debugging (found under "Developer options") set to "ON".
5. "Allow USB debugging" prompt set to "OK" + "Always allow from this computer" checked (This prompt shows up when connected to computer for the first time).
6. Debug build of app you plan to monitor (ask your developer kindly to make one for you). In case your device is rooted, you can monitor any build.	

## Steps:

1. [Download](https://developer.android.com/studio), install and run Android Studio.
2. Click on "New Project".
3. Select "No Activity" and click Next.
4. Set the "Name" and "Android version that isn't above the one you are running on your test device (otherwise Android Studio will notify you with warning).
5. Your device should be visible in top bar, next to green “Play” button (If it isn’t, check "It doesn't work” section).
6. Click on "Profiler" in bottom bar of Android Studio.  
 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:100%;">![2_battery.png](/img/2_battery.png)</span>  
7. Click on "+".  
 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:100%;">![3_battery.png](/img/3_battery.png)</span>  
8. Your test device should be present here.
9. Select it.

 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:100%;">![4_battery.png](/img/4_battery.png)</span>

 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:100%;">![5_battery.png](/img/5_battery.png)</span> 

10. Select app you want to monitor.
In case your app isn't present, try to run it on your device first 
to trigger a refresh in Android Studio.  
11. Session started, only thing left is to click on "Energy" timeline to zoom on battery consumption. 
Monitoring lasts until you press “Stop” button. After stopping, you can inspect recorded session.

The Energy Profiler provides user with insight about where your app uses each of these events and processes so that you can check if there is any excessive impacts on battery.  
For more info about “wake locks’, “alarms” and “jobs” check [this](https://infinum.com/handbook/books/qa/tools/using-adb).

 

## "It doesn't work" 

1. Check if you have ADB installed on your computer, if not sure or answer is "What?" check [this](https://infinum.com/handbook/books/qa/tools/using-adb).
2. Check if you set "USB debugging" to “ON" (Prerequisites section).  
3. Try "Revoke USB debugging authorisations" option, disconnect phone, connect again, accept prompt that shows up.  
4. Try other USB cables.  
	It is not so uncommon to connect phone to computer by micro USB cable, only 	to find out that cable you used can only charge the device ([thicker is 	better](https://www.dignited.com/50330/usb-data-cable-vs-usb-charging-	cable/)).  
	USB-C cables are a bit better in that aspect but even they aren't all same.  
	![6_battery.png](/img/6_battery.png)  
5. Make sure that app you plan to monitor is debug build.  
6. In case you don't see app you want to monitor in Android Studio - try to run it on device first, that should trigger refresh in Android Studio.

## “I don’t want Android studio option”

There is [option](https://developer.android.com/studio/profile/android-profiler#standalone-profilers) to run Android Profiler without running full Android Studio.  
Only requirement is Java installed on computer you are using and that profiler isn’t currently running inside Android Studio.