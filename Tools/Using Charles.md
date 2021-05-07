> People always say "code and then test," I prefer “test and then code."

## Using Charles

[Charles](https://www.charlesproxy.com/) is an HTTP proxy that helps you to view all HTTP/S traffic between the app you are testing and the internet. 
To install Charles on macOS, [follow this handy guide](https://www.charlesproxy.com/documentation/installation/).

## Setup Charles on iOS

To be able to use Charles on iOS you need to do the following: 

1. Open Settings on your iOS device
1. Tap on Wi-Fi
1. Select the network to which your iPhone is currently connected 
1. Tap on "Configure proxy"
1. Tap on "Server" and enter your laptop's local IP address from the macOS Network Utility
2. Tap on "port" and enter 8888

Once done, return to Charles, click on Record and try to open something in Safari on your iOS device to check if Charles is recording your activity. 

## Setup Charles on Android

It differs from device to device, but it usually goes something like this: 

1. Go to “Settings”
1. Go to “WiFi”
1. Long tap on the WiFi network to which the device is currently connected
1. Tap on “Modify network”
1. Tap on “Show advanced options”
1. Under “Proxy” change to “Manual”
1. Under “Proxy hostname” enter your laptop's local IP address from the macOS Network Utility and under “Proxy port” enter 8888

## Example of debugging an API call 

Charles is very helpful for debuging api calls. Let's show one use case: 

There is a restriction request which says that users under age of 18 cannot use the app. You have implemented the logic for restricting young user from entering the app and you want to test it out. But there is only one test user available and it has value of age parameter set to 45. 

This is the case where Charles becomes very handy. You can set a breakpoint to intercept this call. After Charles does the interception, you can manually change the value of model's parameter.

## Setup SSL proxying

1. In Charles go to Proxy > Proxy Settings > Mac OS X and disable it if activated.

2. Connect the device to the same network as your laptop is on (not a network which blocks proxies).

3. Modify the the WiFi connection on your device to use a proxy. You need to set yor proxy host IP address (which is your laptop IP address, on Charles - Help > Local IP address) and you need to set the port number (for example 8888).

4. On the phone use a browser to navigate to [this page](https://chls.pro/ssl) and install the certificate. On iOS you will also have to open Settings and navigate to General > About > Certificate Trust Settings, find the Charles Proxy certificate and enable it.

5. Traffic should now show in Charles. Put a filter to your project to get rid of all the other traffic from your phone. If Charles shows "Unknown" label for all the calls from target api you can right click on it and select "Enable SSL proxying".

![Adjust traffic](/img/charles-focus-and-enable-ssl.png)

## How to use breakpoints

Breakpoints are a very useful feature in Charles. You can use them doing following steps:

Right click on a wanted call and then select "Breakpoints".

![Select breakpoints](/img/charles-breakpoints-select.png)

After that, execute the call and wait for Charles to intercept it. It will also intercept request (you can adjust this in settings). Just click on execute and continue to response. When response is shown, select JSON Text and simply change wanted value. When finished, click execute. And it is simple as that!

![Debug breakpoints](/img/charles-breakpoints-debug.png)

---

![dil-internet.gif](/img/dil-internet.gif)
