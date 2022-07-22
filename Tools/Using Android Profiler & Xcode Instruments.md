> *Only conducting performance testing at the conclusion of system or functional testing is like conducting a diagnostic blood test on a patient who is already dead.*

## How to?

There are many reasons why app is having performance issues, like bad CPU usage, unnecessary memory consumption, poor implementation of battery resources, etc. 

To debug and overcome these issues you can use Android Profiler for Android apps and Instruments for iOS apps.

If testing with these tools and you notice too much CPU is used, battery is draining fast, etc., take a screenshot of profiler and attach it to your task because this will help developer to figure out problem much faster.


## Android Profiler and Instruments

### Android Profiler

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

## Instruments

The Instruments app in Xcode provides a rich set of tools and templates for profiling your app performance.

Although it’s embedded within and may be used with Xcode, Instruments is a separate app, which may be used independently as needed.

To install Xcode, go to App Store and install it from there.

To start using Instruments and profile the app, an iOS developer will need to install a debug build on your device (preferable). There is another option with using any build which doesn't require a developer but has a constraint which is hidden names for all collected data. 

The other option is good if you only need to check overall app performance without digging deep into the data.

How to setup everything is explained below on example of non-debug build.

**Steps:**

1. Connect an iPhone with Macbook and open the app you want to profile (this is important because it won't work if the app is closed).

2. In Xcode, choose **Xcode > Open Developer Tool > Instruments**.

	![](/img/xcode_instruments_menu.png)

3. In the profiling template selection dialog that appears, select a target device and find your app in the Running Applications list.

	![](/img/instruments_profiling_dialog_target.png)
	
	![](/img/instruments_choose_profiling_template.png)
	
4. Select a desired profiling template.

	![](/img/instruments_profiling_dialog_template_choice.png)

5. Click **Choose**.

6. Click the Record button in the toolbar (or press Command-R) to begin recording.

7. Use your app or the system normally.

8. Click the Stop button, or press Command-R again, when complete.

A trace document is used to organize and configure instruments for profiling, initiate data collection, and view and analyze the results.

![](/img/instruments_trace_document.png)

The trace document includes the following main areas:

* [**Toolbar:**](https://help.apple.com/instruments/mac/current/#/dev546b5b54) Allows you to start, pause, and stop data profiling, add instruments, hide and show panes, and more.
	 * Profiling controls: Allow you to record, pause, and stop data collection.
	 * Target device list: Allows you to select the device on which you wish to profile.
	 * Target process list: Allows you to select the process or processes to profile.
	 * Activity viewer: Shows the number of runs for the trace document and the elapsed time of the current trace.
	 * Add Instrument button (+): Shows or hides the instruments Library palette, which contains a complete list of available instruments. From here, you can select individual instruments and add them to your trace document.
	 * View buttons (): Hide or show the detail pane and inspector.
	 
![](/img/instruments_trace_document_toolbar.png)

* [**Timeline pane:**](https://help.apple.com/instruments/mac/current/#/devc12c5417) Displays a graphical summary of the data recorded for a given trace.
	* This pane’s information is read-only, you can scroll through data, select specific areas for closer examination, and insert flags to highlight points of interest.
	* Click the strategy buttons in the filter bar to display instruments, CPU core, thread data, or all three items in the timeline.
		* *CPUs:* Displays a list of CPU cores, along with their usage over time, in the timeline pane. Only available when a trace document contains instruments that record CPU data.
		* *Instruments:* Displays a list of instruments and their corresponding data in the timeline pane. If you select an instrument in the list, you can delete it or configure it in the inspector pane. The instruments list is visible by default when you create a trace document.
		* *Threads:* Displays a list of threads and their utilization data in the timeline pane. Only available when a trace document contains instruments that record thread data.

![](/img/instruments_trace_document_timeline_pane.png)
	
* [**Detail pane:**](https://help.apple.com/instruments/mac/current/#/dev9b08bd72) Shows detailed information about the data collected by the instruments in your trace document.
	* Navigation bar
		* *Instrument:* Icon of the currently selected instrument in the timeline pane. Click this to view the console for the instrument.
		* *Detail type list:* Allows you to navigate between different types of data. The options displayed here vary, depending on the actively selected instrument. For many instruments, the list includes things like a summary of data, a call tree, and a console.
		* *Detail tree:* Keep track of where you are in the hierarchy as you navigate through the data in the detail pane. Click a branch of the tree to move back up the hierarchy to the corresponding data.
	* Collected data area
		* The collected data area shows you all of the data for the selected instrument, typically in tabular format. The content displayed here varies significantly from instrument to instrument. For example, the Activity Monitor instrument displays process, CPU, and thread information, and much more.
	* Filter and configuration bar
		* *Filter field:* Allows you to filter collected data for a specific term. Click the filter field’s menu for some additional filtering options. You can also filter collected data more extensively by adjusting display settings in the display configuration popover.
		* *Display configuration controls:* Refine the displayed results by filtering, sorting, and data mining. The controls vary from instrument to instrument and can include menus for selecting different views of the results, and popovers for constraining the data that is shown.

![](/img/instruments_detail_pane.png)

* [**Inspector pane:**](https://help.apple.com/instruments/mac/current/#/devd72c957d) Contains summary information about the current data record and instrument specific extended detail.
	* *Run information area:*  The run information area shows information about the run displayed in the detail pane including the target, recording time, and the settings used for the recording.
	* *Extended detail area:* The extended detail area is used to display additional instrument-specific information about selected data in the detail pane, such as a complete stack trace.

![](/img/instruments_inspector_pane_navigation_bar.png)

In the [Instruments documentation](https://help.apple.com/instruments/mac/current/#/) you can find additional options this tool can give you like tracking CPU core and thread use, find performance bottlenecks and memory leaks, etc. You can even find [zombies](https://help.apple.com/instruments/mac/current/#/dev612e6956), I kid you not.
