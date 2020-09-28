> *Quality is free, but only to those who are willing to pay heavily for it.*

## The Basics

Prince of Versions is a lib we use on mobile platforms that enables us to easily notify users of optional and mandatory updates to their app.

**Mandatory update:**

A mandatory update is needed when a user uses an app that is well overdue for an update. Eg. When a big update comes to the app or the backend of the app. The user has to update the app to continue using it.

**Optional update:**

Optional update is used when the app is still usable, but we wish to notify the user that there is a newer, better version. The user can decline the update and continue using the app normaly.

The only difference between the two is the option to close the notification for updating the app. Mandatory update does not allow further usage of the app without the update, while the optional update does. Example:

![](/img/mandatory-update.png)

You can notice that there is no back arrow or "X" to close the notification.

**Optional update** can and should use the same window but with back/"X" options included.

Prince of versions is a JSON library developed by Infinum, for smoother and quicker version control for installed apps. It's basically a JSON file that looks like this:

```
{
	"ios": {
		"minimum_version": "1.2.3",
		"latest_version": {
			"version": "2.4.5",
			"notification_type": "ALWAYS"
		}
	},
	"android": {
		"minimum_version": "1.2.3",
		"minimum_version_min_sdk": 15,
		"latest_version": {
			"version": "2.4.5",
			"notification_type": "ONCE",
			"min_sdk":18
		}
	},
	"meta": {
		"key1": "value1",
		"key2": "value2"
	}
}
```

Depending on platform, we have different attributes, and they are as follows:

```
"minimum_version": "1.2.3"
```
- This attribute tells us which version of the app is the latest supported one. It checks if mandatory update is needed.

    For example - If the app is on version **1.2.2**, during app start there should be a screen that notifies the user that he is using a very outdated version of the app and that the update is mandatory for further use (the user should not be able to close this screen)

```
"minimum_version_min_sdk": 15
```

- Mandatory update notification will be shown only on those devices that have SDK version 15 or greater (Android 4.0). If the app is downloaded to a device with SDK 14 or less, mandatory update screen will not be shown - That means that the updated version is not supported by devices with SDK 14 or less.

```
"latest_version": {
			"version": "2.4.5",
			"notification_type": "ONCE",
			"min_sdk":18
		}
```

- This part of the JSON file checks if the optional update screen should be shown

	```
	"version": "2.4.5"  
	```

	- This attribute checks if the version of the device is lesser than the one specified.

	
	For example - If you want to test the optional updates, and the device has app version "2.4.5", all you need to do is change this attribute to, in this case, "2.4.6" and save the changes. The prince of versions should automaticaly see that you do not have the latest version of the app.

	```
	"notification_type": "ONCE"
	```

- Depending on this setting (ONCE or ALWAYS), the optional update screen will be shown a number of times. This **does not** apply to mandatory update, it has to be shown every time. If this attribute is set to "ONCE", optional update screen will be shown when first starting up the app. Every time the user starts the app, if that screen was shown, the screen for optional update will not be shown. To show the update screen every time the user starts the app set the attribute to "ALWAYS".

	```
	"min_sdk":18
	```

- This attribute refers to lowest Andriod version supported by this update. In case the device has SDK of 17, the optional update screen will not be shown, even if the device has a lower version app than the attribute "version"

```
"meta": {
		"key1": "value1",
		"key2": "value2"
	}
```

- These parameters are optional and they are usually String type. They are commonly used for marking the URL for the latest update

## Production build testing

### Android:

**Mandatory and Optional update:**

**Test case 1:**

1. Install the latest build in production (from the Play-store) and **Activate a token** - Build 1.2.2.
2. Edit the JSON file - Change `"minimum_version": "1.2.3"`
3. Open the build you downloaded and check if there is a Mandatory update screen

**Test case 2:**

1. After the Mandatory update screen is shown, press "Update"
2. At that moment, the app will probably open Play-store
3. The idea is to download the latest beta build over mandatory updates
4. Do a regression test and check if the token is still active

**Test case 3:**

1. If everything is going smoothly, you need to edit the JSON file once more
2. This way we confirm, that the Prince of Versions works on new builds as well
3. By editing the JSON file we can test both(but not at the same time) mandatory updates (by changing `"minimum_version": "1.2.3")` or optional updates (by changing `"version": "2.4.5"`)

Once again be very carefull when editing the JSON file, as it affects **all** users on that version of the app (staging or production)

**Test case 4:**

1. You should also test the `"notification_type":` parameter
2. In the JSON file, we need to set `"notification_type": "ONCE"` and open the app
3. When the update screen is shown, close it or back out from it
4. Force close the app and restart it
5. The optional update screen should not be shown.
6. Set the `"notification_type": "ALWAYS"` and restart the app
7. No matter how many times you close the app, the screen for the optional update should be shown on every app start.

###iOS:

**Mandatory and Optional update:**

**Test case 1:**

1. Install the latest build in production (from the Play-store) and **Activate a token** - Build 1.2.2.
2. Edit the JSON file - Change `"minimum_version": "1.2.3"`
3. Open the build you downloaded and check if there is a Mandatory update screen

**Test case 2:**

1. After the Mandatory update screen is shown, press "Update"
2. At that moment, the app will probably open the App-store(or TestFlight for beta)
3. The idea is to download the latest beta build over mandatory updates
4. Do a regression test and check if the token is still active

**Test case 3:**

1. If everything is going smoothly, you need to edit the JSON file once more
2. This way we confirm, that the Prince of Versions works on new builds as well
3. By editing the JSON file we can test both(but not at the same time) mandatory updates (by changing `"minimum_version": "1.2.3")` or optional updates (by changing `"version": "2.4.5"`)

Once again be very carefull when editing the JSON file, as it affects **all** users on that version of the app (staging or production)

**Test case 4:**

1. You should also test the `"notification_type":` parameter
2. In the JSON file, we need to set `"notification_type": "ONCE"` and open the app
3. When the update screen is shown, close it or back out from it
4. Force close the app and restart it
5. The optional update screen should not be shown.
6. Set the `"notification_type": "ALWAYS"` and restart the app
7. No matter how many times you close the app, the screen for the optional update should be shown on every app start.

<span style="color:red">** These tests can be done by using Charles to edit the PoV response.**</span>


## Test build testing

**Mandatory and Optional update:**

**Mandatory update: First method**

Steps:

1. Download any version of the app from Labs(except the latest one) and install it

2. Open that project on labs.infinum.co and go to the latest version. For example:

![](/img/labs1.png)

3. Click on the three dots and then "Edit release"

![](/img/labs2.png)

4. After that mark the checkbox "Minimum version"

![](/img/labs3.png)

5. When that is set, all builds before that one, will be treated as "outdated". They will have a mandatory update screen

**Mandatory update: Second method**

Mandatory update can also be tested by modifying the JSON file on the Environments page

Steps:

1. Navigate to Environments page

![](/img/POV Testing 1.png)

You can check the current format and data of the JSON for a specific environment by clicking on the “LINK”

![](/img/POV 2.png)

2. To change the data in the JSON file for a specific environment, first, click on the Environment you are testing. 
	- also be aware to select the correct platform here - iOS or Android

![](/img/POV3.png)

3. Under the Prince of Versions field paste the JSON with the desired edited data - "minimum_version" set above the version currently installed

![](/img/POV last.png)

4. When that is set, all builds before that one, will be treated as "outdated". They will have a mandatory update screen

**Optional update**

Optional update can also be tested in the similar way, this time "latest_version" field needs to be changed in the JSON file. It needs to be set above the version currently installed.


---

![testing-prince-of-versions.gif](/img/testing-prince-of-versions.gif)
