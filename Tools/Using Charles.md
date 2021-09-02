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
1. Tap on "Server" and enter your laptop's local IP address (find it in macOS' Network Preferences)
1. Tap on port and enter "8888"

## Android setup

It differs from device to device, but it usually goes something like this: 

1. Go to “Settings”
1. Go to “Wi-Fi”
1. Long tap on the Wi-Fi network to which the device is currently connected
1. Tap on “Modify network”
1. Tap on “Show advanced options”
1. Select "Manual" in the “Proxy” menu
1. Under “Proxy hostname” enter your laptop's local IP address (find it in macOS' Network Preferences) and under "Proxy port" enter 8888

---

After several seconds, you should get a prompt in Charles asking you to confirm traffic coming from your device. 

If that does not happen, try restarting Charles. Now you will see all the traffic that your device is sending out and receiving, but it will be encrypted if done via a secure protocol (HTTPS).

## SSL proxying setup

To see HTTPS traffic in plaintext, you will have to set up SSL proxying:

- After connecting to your laptop/Charles, use a browser on the mobile device to navigate to https://chls.pro/ssl and download the Charles certificate.
- Install the certificate. 
- On iOS you will also have to open Settings and navigate to General > About > Certificate Trust Settings, find the Charles Proxy certificate and enable it.

Now you should be able to "Enable SSL proxying" on an endpoint you are interested in and see unencrypted traffic in both directions.

Note: the above will not work if there is a pinned certificate in the app.

![Adjust traffic](/img/charles-focus-and-enable-ssl.png)

## How to use breakpoints

Breakpoints enable you to stop requests/responses "mid-air" (in Charles) and change them before forwarding them back to the API or to the mobile app.
By doing so, you effectively take full control of all the networking. :)

To set up a breakpoint, right-click on an endpoint and select "Breakpoints":

![Select breakpoints](/img/charles-breakpoints-select.png)

After that, execute some requests in the mobile app towards that endpoint and wait for Charles to intercept them. 

Now you will be able to change the request before executing it if you wish to do so. You will also be able to change the response before forwarding it to the phone.

![Debug breakpoints](/img/charles-breakpoints-debug.png)

If you want to rewrite requests and responses automatically, you can use [Charles' Rewrite tool](https://www.charlesproxy.com/documentation/tools/rewrite/).

## Exporting traffic to a HAR file

You can multi-select several requests and export them as HAR files, just make sure to select the HTTP Archive (.har) format

Now you will have a file that is basically a snapshot of the all the requests you’ve made and all the responses received.

Why would you that? One possible use case is to convert that HAR file to a k6 script and get a load test for free. :) See [Performance - API](https://infinum.com/handbook/books/qa/tools/performance-api) for more details.

## Repeating requests

Let's say you have to create 100 articles in the mobile app you are testing to satisfy the preconditions for a certain test case. Let's also assume you don't have access to API docs or a Postman collection that could come in handy.

These are some of your options:

- You could create them manually in the mobile app, but that's boring and surely not the optimal way to do it.
- You could ask a developer to add them to the database directly, but now you're just delegating work.
- Finally, you could create one article and use that request to create 99 more of them.

Charles can help you achieve the 3rd option. Just isolate the request you want to repeat, right-click on it, and select "Repeat Advanced".

Once you enter the amount of iterations, click on "Ok" and watch Charles do his magic.

![repeat.png](/img/repeat.png)

If you want even more flexibility, you can right-click on the request, select "Copy cURL request" and get a nice cURL command that's good to go:

```
curl \
'https://api.foo/api/v1/resource' \
-H 'accept: application/vnd.api+json' \
-H 'authorization: mytoken' \
-H 'content-type: application/vnd.api+json' \
-H 'accept-language: en-GB' \
--data-raw '{"data": "mydata"}' \
--compressed
```

Now just add `repeat 99` in front of your cURL command, execute it in your terminal of choice, and you're off to the races. :)

The nice thing with cURL commands is that you can easily share them with the rest of the team.

---

![dil-internet.gif](/img/dil-internet.gif)
