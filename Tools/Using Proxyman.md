> *Before software can be reusable it first has to be usable.*

## About Proxyman

[Proxyman](https://proxyman.io/) is an HTTP proxy / HTTP monitor / Reverse Proxy that helps you to view, inspect, and manipulate all of the HTTP and HTTPS traffic between the app you are testing and the Internet.

### Why Proxyman?

* It is relatively easy to use even for newbies 
* For quick testing whether you are a tester or developer 
* It's basically the same tool as [Charles](https://infinum.com/handbook/books/qa/tools/using-charles) but it has a few more features 
* It can be used to share VPN from Mac to your mobile device 

### When Proxyman?

Let's say you have a circle chart that on a scale of 0-100% is displaying occupancy of some building. A chart is not only showing the correct value but it is changing color depending on it. 
If occupancy is between 0-60%, the value is green. If occupancy is between 60-80% value is yellow, and if occupancy is between 80-100% value is red.

![Proxyman_charts.png](/img/Proxyman_charts.png)

Since value depends on data received from sensors and you cannot simply change it, here is where Proxyman becomes very handy. Setting a breakpoint and intercepting a call you can manually change and test some specific cases such as:

* Custom values on the chart
* If a chart is showing the correct color for a given value
* You can test extreme cases, for example, how would the chart look like if a value is below 0%, or if a value is above 100%
 
## Proxyman on MacBook

To install Proxyman on your Mac just download the latest version from [here](https://proxyman.io/). 

### Certificate install 

After installation, you are required to install a certificate on your Mac:  

1. Open Proxyman 
2. Click on the "Certificate" tab 
3. Click "Install Certificate on this Mac"
4. Follow instructions and install Certificate

Once it is done, you will see that your certificate is installed & trusted. 

![Proxyman_crtificate.png](/img/Proxyman_crtificate.png)

### Breakpoint Tool 

Breakpoint Tool (Breakpoints in Proxyman) is used for stoping a request before it goes to a server or for stoping a response before it goes to the app. To do that, Proxyman is using "Breakpoint rules". In rules, you define the API URL that you want to intercept and whether if you want to intercept a request or response. You can also name your rule so it is easier for you to find it later in the list of rules.

To use breakpoints, first you need to define the breakpoint rule. 

1. In toolbar click on **Tools** dropdown menu 
2. Click **Brakepoint** > **Rules**. Or you can access it by pressing ⌥ +⌘ + B
 <span style="display:block; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:100%;">![Proxyman_brakepoint.png](/img/Proxyman_brakepoint.png)</span>
3. Click the "+" button (bottom left corner of the breakpoint rules screen)
4. Add the name of the rule 
5. Enter the desired URL to the "Matching Rule" input field 
6. If you click "ANY", you can choose in between HTTP requests. Most of the time "ANY" would be just fine  
7. Select whether you want to use this rule for interception of your request, response or it can be used for both 

![Proxyman_rule_draft.png](/img/Proxyman_rule_draft.png)

Great now you have a rule. If you click "+" you can add a new rule and create a list of rules. You can completely edit the existing rule by double-clicking on it or you can quickly enable/disable or change the request or response by clicking on the checkboxes of the desired rule in the list. 

![Proxyman_brakepoint_rules.png](/img/Proxyman_brakepoint_rules.png)

### Change of response

After you refresh the page in your app, Proxyman will open a breakpoint window that will show you "Request" and "Response" in JSON format. In **Response**  on the right part of the screen, switch to the "Body" tab. In this example, we will edit the average utilization value. The initial value is 20, but we now want to see if the value of 89% is displayed correctly. Let's edit **avgUtilization** and set it to 89. 

![Proxyman_value_89.png](/img/Proxyman_value_89.png)

After editing, by clicking on the **Execute** button the edited response will be displayed in the app. 

<span style="display:block; border: 1px solid #e0e0e0; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:100%;">![Proxyman_example_chart.png](/img/Proxyman_example_chart.png)</span>

Every time you want to apply a different value, you need to refresh the page, enter the desired value and execute the response.

**TIP**: After you finish, make sure that you either unselect breakpoints that you will not use anymore or delete them because as long as Proxyman is turned on and you are triggering this API call (some calls are automatically triggered every 30 sec) Proxyman will intercept it and the breakpoint window will be opened.

This was an example of manipulation with a response. In the same way, you can manipulate with a request. 

## Proxyman on iOS and Android devices

Before using Proxyman on your mobile device you need to install certificates and set up a proxy. 

### iOS device

1. Open Proxyman on your Mac
2. Click on the "Certificate" tab
3. Click "Install Certificate on iOS"
4. Click "Physical Devices"
5. Follow instructions and configure Wifi Proxy on iOS device to Proxyman
6. Follow instructions and install the Certificate on your iPhone 

### Android device

It differs from device to device but it can go something like this: 

1. Open Proxyman on your Mac
2. Click on the "Certificate" tab
3. Click "Install Certificate on Android"
4. Click "Physical Devices"
5. Follow instructions and configure Wifi Proxy on Android device to Proxyman
6. Follow instructions and install the Certificate on your Android device (be careful, trusting Proxyman Certificate is different for Android 7+ and Android 11+ devices)

Once done, you can now add rules and start using Proxyman on your mobile devices. 

## Sharing the VPN from your Mac to your mobile device
 
Sometimes you'll be in a situation where you need to use a VPN on your mobile device and instead of setting up VPN on your mobile device, you can use Proxyman as a VPN sharing tool.

### On your MAC

1. Connect to a Wi-Fi network
2. Connect to a proxy
3. While holding the Option key (⌥), click the Wi-Fi icon in your Mac's status bar
4. Remember the IP address

 ![IP address](/img/proxyman1.png)
 
### On your iPhone

1. Open up Settings
2. Tap on Wi-Fi
3. Connect to the same network as the one you're connected to with your Mac
4. Tap on configure proxy
5. Tap on "Server" and write down your IP address (the one you remembered)
6. Tap on "Port" and write down 9090

 ![iOS proxy setup](/img/ios_proxy_setup.gif)
 
### On your Android

It differs from device to device but it can go something like this:

1. Go to "Settings"
2. Go to "Wifi" or "Network"
3. Connect to the same network as the one you're connected to with your Mac
4. Long tap on the Wifi network you are connected to
5. Click the "Modify network" option
6. Click "Show advanced options"
7. Under "Proxy", change the option to "Manual"
8. Tap on "Proxy hostname" and write down your Mac's IP address (the one you remembered)
9. Tap on "Proxy port" and write down 9090

 ![Android setup](/img/android_proxy_setup.gif)
 
Once you are done, you'll "share" the VPN from your Mac on your mobile device.

---
![dil-robot.gif](/img/dil-robot.gif)
