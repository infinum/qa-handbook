> People always say "code and then test," I prefer “test and then code."

[Charles](https://www.charlesproxy.com/) is an HTTP proxy that helps you to inspect HTTP/S traffic. For the purposes of this tutorial, we will focus on Charles as a man-in-the-middle between the app you are testing on a mobile device and the Internet. 

## Charles setup

- Install Charles on your laptop and run it.
- Turn off macOS proxying and Firefox proxying in the Proxy menu because we just want the data stream from the phone/tablet.

## iOS setup

To be able to use Charles on iOS you need to do the following: 

1. Open Settings on your iOS device
1. Tap on Wi-Fi
1. Select the network to which your iOS device and your laptop are currently connected
1. Tap on "Configure proxy"
1. Tap on "Server" and enter your laptop's local IP address (find it in the macOS Network Utility)
1. Tap on port and enter "8888"

## Android setup

It differs from device to device, but it usually goes something like this: 

1. Go to “Settings”
1. Go to “Wi-Fi”
1. Long tap on the Wi-Fi network to which the device is currently connected
1. Tap on “Modify network”
1. Tap on “Show advanced options”
1. Select "Manual" in the “Proxy” menu
1. Under “Proxy hostname” enter your laptop's local IP address (find it in the macOS Network Utility) and under "Proxy port" enter 8888

---

After several seconds, you should get a prompt in Charles asking you to confirm traffic coming from your device. 

If that does not happen, try restarting Charles. Now you will see all the traffic that your device is sending out and receiving, but it will be encrypted if done via a secure protocol (HTTPS).

## SSL proxying setup

To see HTTPS traffic in plaintext, you will have to set up SSL proxying:

- After connecting to your laptop/Charles, use a browser on the mobile device to navigate to [this page](https://chls.pro/ssl) and download the Charles certificate.
- Install the certificate. 
- On iOS you will also have to open Settings and navigate to General > About > Certificate Trust Settings, find the Charles Proxy certificate and enable it.

Now you should be able to "Enable SSL proxying" on an endpoint you are interested in and see unencrypted traffic in both directions.

Note: the above will not work if there is a pinned certificate in the app.

![Adjust traffic](/img/charles-focus-and-enable-ssl.png)

## How to use breakpoints

Breakpoints enable you to stop requests/responses "mid-air" (in Charles) and change them before forwarding them back to the API or to the mobile app.

To set up, a breakpoint, right-click on an endpoint and select "Breakpoints":

![Select breakpoints](/img/charles-breakpoints-select.png)

After that, execute some requests in the mobile app towards that endpoint and wait for Charles to intercept them. 

Now you will be able to change the request before executing it if you wish to do so. You will also be able to change the response before forwarding it to the phone.

![Debug breakpoints](/img/charles-breakpoints-debug.png)

---

![dil-internet.gif](/img/dil-internet.gif)
