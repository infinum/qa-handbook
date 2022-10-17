> Only conducting performance testing at the conclusion of system or functional testing is like conducting a diagnostic blood test on a patient who is already dead. - Scott Barber

## How to?

There are many reasons why an app is having performance issues, like bad CPU usage, unnecessary memory consumption, poor implementation of battery resources, etc. 

To debug and overcome these issues you can use Android Profiler for Android apps.

If testing with this tool and you notice too much CPU is used, battery is draining fast, etc., take a screenshot of the profiler and attach it to your task because this will help developers to figure out the problem much faster.

## Android Profiler

The Android Profiler tools provide real-time data to help you to understand how your app uses CPU, memory, network, and battery resources.

Profiling ("program profiling", "software profiling") is a form of dynamic program analysis that measures, for example, the space (memory) or time complexity of a program, the usage of particular instructions, or the frequency and duration of function calls.

You will need Android Studio for this, go ahead and download it from this [link](https://developer.android.com/studio) and install it.

The Android Profiler is compatible with Android 5.0 (API level 21) and higher.

There are two ways to start profiling:

1. You will need debug APK file.
2. You will need an access to the codebaase.

You want to have debug APK because it is much easier and faster solution. If there is no debug APK, ask developer to build one for you. They always work with debug APK and it's not time consuming or complex for them to do it for you.

**Steps:**

1. Open Android Studio.

2. Select "Start a new Android Studio project".
	
	![](/img/Android_Studio-start_new_project.png)

3. Select "Add no activity" and click on Next button.

	![](/img/Android_Studio-add_no_activity.png)

4. On "Configure your project" step, you can change project name, where to save the project, etc. You can only change Minimum API level to API level 21. Click on Finish button.

	![](/img/Android_Studio-configure_your_project.png)
	
	You just created an empty project.
	
5. Connect Android device with USB cable to Macbook and make sure USB debugging is enabled.

6. In Android Studio, the connected device will be shown.

	![](/img/Android_Studio-connected_device.png)

7. Now you need to set up Profiler by going to **File > Profile or debug APK > Select APK File** (choose debug APK file you want to profile) > click OK.

8. After APK file is loaded, go to **Run > Profile**.

	![](/img/Android_Studio-Run_and_Profile.png)

9. The app will open on your device. Profiler will start with collecting profiling data until you disconnect the device or click End Session.

**Android Profiler shared timeline view**

![](/img/Android_studio-Profiler.png)

1. Android Profiler shows the process and device currently being profiled.

2. In the Sessions pane, choose which session to view, or start a new profiling session.

3. Use the zoom buttons to control how much of the timeline to view, or use the Attach to live button to jump to the real-time updates.

4. The event timeline shows events related to user input, including keyboard activity, volume control changes, and screen rotations.

5. The shared timeline view, which includes graphs for CPU, memory, network, and energy usage.

**Profilers**

[**Network Profiler**](https://developer.android.com/studio/profile/network-profiler) - The Network Profiler displays realtime network activity on a timeline, showing data sent and received, as well as the current number of connections

[**Energy Profiler**](https://developer.android.com/studio/profile/energy-profiler) - The Energy Profiler monitors the use of the CPU, network radio, and GPS sensor, and it displays a visualization of how much energy each of these components uses

[**Memory Profiler**](https://developer.android.com/studio/profile/memory-profiler) -  The Memory Profiler can help you identify memory leaks and memory churn that can lead to stutter, freezes, and even app crashes

[**CPU Profiler**](https://developer.android.com/studio/profile/cpu-profiler) - The CPU Profiler is used to inspect your app’s CPU usage and thread activity in real time while interacting with your app, or you can inspect the details in recorded method traces, function traces, and system traces
