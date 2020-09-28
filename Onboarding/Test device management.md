> *Testers don’t break software, software is already broken*

## Intro

- Test Lab responsible person (device administrator): Filip Ambruš

- The list of test devices can be found [here](https://docs.google.com/spreadsheets/d/1ttmpe-ZuKQY4SAxtmVgl5Q3MfytPWcY29dJePEKRUb4/edit#gid=1483315145 "awesome souce").

- The list of test SIM cards can be found [here](https://docs.google.com/spreadsheets/d/1fSOrhScMlBDPPeBc70RfD3Xhqc-iQ0BwlESYStDn5wU).

## When using a device

1. You should always change the name tag on the shelf when someone has borrowed it from you
2. You shouldn't leave a display turned ON overnight
3. You should always check if it's ok with the team to update the device to the latest available OS. This depands on various factors, but the most important thing is to keep the same devices on various operating systems
4. Keep the home screen clean
5. **Turn OFF** the VPN or proxy if this is something you've been using before returning the device

## Keep in mind

- You should never return the phone with changed "Don't keep activities", "Accessibility" or any similar setting to the shelf. This could cause a lot of troubles to any device borrower in the future.

- You should never return the phone with an empty battery. Feel free to use the charging cable from the drawer across the testing shelf.

- You should never return a phone with turned ON proxy or VPN.

- You should never return a phone with WiFi throttling ON.

- You should never return a broken phone. Please report any hardware or software issue you may find. It will never be fixed if nobody knows about it.

- You should never return the phone if you're logged in some private service (slack, mail, productive or any other). There are many trolls around us. :)

- You should never return a phone with the screen timeout turned OFF.

- You should never update any device to a major OS version before consulting with other colleagues (we have limited number of devices with different OS versions)

- Old rule, but worth mentioning - each time when you borrow a device (especially if you took it from someone's desk), you should change the name tag on the shelf.

- You should always return device to the shelf at the end of the business day (in case you're not doing any permanent testing which demands longer testing sessions)

- In case you need the test device for more than a day (to perform any remote testing), you have to inform device administrator so that the device change can be updated in the inventory

- Once you return the test device which has been borrowed you need to inform the device administrator so it can be reassigned to the QA inventory again

- In case you take the test device for more than a day without "claiming" it, device administrator is allowed to give you a yellow card.

- Each device has it's own place on the shelf (model name and OS version). If that's not the case, please inform device manager so he can update it.

## How to set up an Android device

1. Factory reset.
2. Connect to the **Infinum** WiFi
3. After going through on-boarding steps, use the **test.infinum@gmail.com** mail for the login (password is available in 1Password app)
4. Use data from the old device, or setup as a new one. The applications that should be installed are listed at the bottom
5. Uninstall bloatware apps if possible
6. Install all minor updates
7. Enable Developer options and the following: Stay awake, USB debugging, Show touches
8. Set the _classic_ lock pattern and/or unlock PIN 1111

	![lock-pattern.jpg](/img/lock-pattern.jpg)
9. Enable installation from **Unknown sources**
10. Use the label maker to print a label with the following content:

	```
	MANUFACTURER Model
	Major Android version
	```
11. Group often used apps in a single folder on the phone's home screen
12. Add the device in the proper sheet ("Android devices" in this case) in this [document](https://docs.google.com/spreadsheets/d/1ttmpe-ZuKQY4SAxtmVgl5Q3MfytPWcY29dJePEKRUb4/edit#gid=1483315145)


### Default Android apps

- File explorer: Amaze
- File transfer: Send Anywhere
- Screen recorder: Mobizen, AZ recorder (it's important to turn OFF the sound recording feature after installing these tools so as not to record any background sounds from the office)
- GPS mocker: Fake GPS, Lockito
- QR scanner: Barcode scanner
- Social: Twitter, Facebook, Instagram
- Other: Dropbox, AnyConnect, OpenVPN

## How to set up an iOS device

1. Factory reset.
2. Connect to the **Infinum** WiFi
3. After going through on-boarding steps, use the **infinum1@icloud.com** mail for the login (password is available in 1Password app)
4. Use data from the old device, or setup as a new one. The applications that should be installed are listed below
5. Set the _PIN_ unlock method to **1122**
6. Use the label maker to print a label with the following content:

	```
	MANUFACTURER Model
	Major iOS version
	```
7. Group often used apps in a single folder on the phone's home screen
8. Add the device in the proper sheet ("iOS devices" in case) in this [document](https://docs.google.com/spreadsheets/d/1ttmpe-ZuKQY4SAxtmVgl5Q3MfytPWcY29dJePEKRUb4/edit#gid=1483315145)

### Default iOS apps

- Browser: Chrome
- QR scanner (if iOS < 11): QR code scanner
- Social: Twitter, Facebook, Instagram
- Google: Gmail, Youtube, Drive
- Other: Dropbox, AnyConnect, OpenVPN

## How to deal with a malfunctioning device

- If you see anything strange with the device's behavior, report this to device administrator
- If the battery looks "inflated", remove it immediately and report this to the device administrator

---

![test-device-management.gif](/img/test-device-management.gif)
