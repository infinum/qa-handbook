>*“Never allow the same bug to bite you twice.” Steve Maguire*

Android Vitals is a part of the Google Play Console that allows you to have a deeper insight
into the stability of your app on Android devices up to the last 3 months.

It can be accessed by navigating to your app on **[Google Play Console](https://play.google.com/console)** and in the menu on the
left dropdown the “Android vitals”. From there, you can access Overview, Performance,
Crashes and ANRs, and App size options with unique insights into the performance of the
app.

Selecting the “Crashes and ANRs” option will show you a list of issues based on how
frequent they are, from there, you can choose any issue and inspect it more thoroughly.
The details screen will contain information about the failed method, such as the number of
affected users and graphs depicting the affected users' setup (App version, OS version,
device). You can also inspect the stack trace for more information about the occurrence of
the issue.

The "App size" option shows a comparison of the size of your app and the average size of
the apps in your peer group, as well as the difference between older versions of your app.
You are also offered recommendations for optimizing the size of your app.

The “Performance” dropdown menu offers the possibility to improve your app’s performance
by integrating the Android Performance Tuner, which enables you to find the most effective
way to deliver the best possible experience to each of your users by helping you to measure
and optimize frame rates, graphical fidelity, loading time, and loading abandonment across
many Android devices at scale.

The most useful tool to you as a developer is the “Overview” option, where you are
presented with graphs depicting your app's performance compared to the peers’ median and
the bad behaviour threshold. Going into details, you are able to filter out the behaviour by
app version (“Artifact”), Android OS version, device, and location of the user. By choosing
“View details” under one of the graphs, you will be navigated to the “Android vitals details”
page with detailed information about the performance of the app split into five tabs.

### Stability

Under the stability tab, you can go into details about crashes and “App not responding”
rates.

* User-perceived ANR/Crash rate - the percentage of daily active users who have
noticed an ANR or crash
* ANR/Crash rate - the percentage of daily sessions with at least one ANR/Crash
* Multiple ANR/Crash rate - the percentage of daily sessions with at least two
ANRs/Crashes

### Loading

The Loading tab gives you insight into the startup times of your app.

*Cold start is when the app is completely closed, and warn start is when you kill the app and
then immediately open it again, in which case all app processes have not been killed yet so
the start of the app is a bit faster than the cold start. Hot start is opening the app from the
background.*

* Slow cold start - the percentage of daily sessions with at least one cold startup time
of more than five seconds
* Slow warm start - the percentage of daily sessions with at least one warm startup
time of more than two seconds
* Slow hot start - the percentage of daily sessions with at least one hot startup time of
more than 1.5 seconds

### Rendering

The Rendering tab examines how fast your app displays frames on the screen

* Excessive slow frames - the percentage of daily sessions with more than 50% of
slow frames
* Excessive frozen frames - the percentage of daily sessions with more than 0.1% of
frames with a time longer than 700 ms

### Battery

Under the battery tab, you are given a better insight into the excessive usage of the users’
battery

* Excessive wake-ups - the percentage of sessions in which the app averaged more
than 10 wake-ups per hour
* Stuck partial wake locks (background) - the percentage of sessions in which the app
had one or more partial wake locks per hour while in the background
* Excessive background Wi-Fi scans - the percentage of sessions in which the app
averaged more than four WiFi scans per hour while in the background
* Excessive background network usage - the percentage of sessions in which the app
used more than 50 MB of network data per day while in the background

### Permissions

Here you can see the percentage of users who have denied permissions to your app

* The percentage of daily sessions in which the user denied your app at least one
requested permission
* You are able to see the percentage of permissions denied per app version, android
version, permission group, device, and country/region
* Unlike other data, permission denials are not compared to the peers’ median