> *The most exciting phrase to hear in science, the one that heralds discoveries, is not ‘Eureka!’ but ‘Now that’s funny'...*

### Why is prerelease testing an important part of the release process?

To ensure the quality of our products we need to make sure that newly developed features did not disrupt old ones and that old ones still work as expected. 
Because of that, before every release, it is crucially important to do a regression test and confirm that both newly developed and old features work in the best way possible.

### Things that should do done before you even start testing

Whether it is a release of mobile or web apps, make sure all features are merged in the release candidate build and that the respective backend features are deployed to your test environment. Once this is done, you can start doing your magic. 

## Mobile Apps

### Preparation is the key!

- Have your test cases ready before going into regression testing.
- Create a test plan (If it is available in a tool where you keep test cases) and test execution (Test run) with all test cases related to the current release. 

**TIP:** Name your test execution as specific as possible - it will be easier for you to find it later. :)
For example, name the platform on which you are performing regression test and release version, you can also add a name (ticket number) of the test plan if it is available. 

- Make sure to discuss the scope and effort needed with your team. If you are doing a regression test for the first (Whether you just started your QA career or you are the first time on a project) make sure to take enough time to complete it.
- Make sure your test environment is as close as possible to production.
- If you have automated parts of the app, focus on manually testing those parts that were left unchecked, but don't completely ignore those that were covered.

### Choosing mobile devices for regression test

There is no silver bullet when it comes to choosing devices for your regression test. The first step would be to find out all the supported devices and the minimum supported version of OS. 

The ideal would be to do a regression test on all of them but most of the time because of limited time for testing it is not possible. 

The best practice would be to check which mobile devices are the most used and from them take the two most common ones. Also, make sure that one device has the most used OS and another minimum supported version of it.

If you have some extra time you can do at least a smoke test on some other supported/most used devices.

**TIP:** Mix it up - don't use the same devices from regression test to regression test. In that way, you'll be covering more of the spectrum each time you do it. 

### Testing, testing, and more testing...

- Run a regression test of the release candidate on a non-production environment by following the test cases from test execution.

Sneak pic how typical test execution looks like in TestRail:

![Testing_Prereleases_TestRail.png](/img/Testing_Prereleases_TestRail.png)

At the top, there is an overview with this fancy pie chart that shows your progress (how many test cases passed, failed, are blocked...) and underneath there are test cases. Pay attention to the naming of the regression test and used devices :) 

- Make sure to check the [Prince of Versions](https://infinum.com/handbook/books/qa/testing/testing-prince-of-versions) scenarios for mandatory and optional updates.
- Report bugs as soon as possible after uncovering them. Make sure that you discuss them with a team so they can be prioritized, fixed, and a new build can be created for you to continue testing ASAP.
- Retest the affected area of the app in each test candidate.

#### Pro Tip 1: Communicate all the way

Keep informing the project team of your progress in daily meetings or via Slack. Let them know if you have any problems, you need help or you just need more time to finish your testing.

#### Pro Tip 2: Do not complicate things too much

Don't go too deep into all the features, optimize testing in a way to touch all areas of the app but also focus on those features that are truly critical and/or have been affected by the new release.

#### Pro Tip 3: Rely on your instincts 

Make exploratory testing part of your regression test. The test cases themselves are a great guide, but you should rely on your instinct as well.

#### Pro Tip 4: Finish your testing

The app should not go to production before you went through all test cases in your test execution. After that, you will have a good app overview and it is good enough for release or not. 

### What to do after testing?

Once all blockers are fixed and the app is ready for release, share and discuss test results with your team. Type down a short report and share it in the project group via Slack or use your daily meetings to do so.

Most of the tools (Such as Jira and TestRail) have the option to create test report documents in PDF format. This comes in handy when you need to share a report with a client.
Here is just an example of how a generated report from TestRail looks like:

<span style="display:block; border: 1px solid #e0e0e0; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:100%;">![Testing_Prereleases_Report.png](/img/Testing_Prereleases_Report.png)</span>

#### 3,2,1 Launch!

The app will be submitted to its respective store and once approved it will be released to a limited part of the audience (phased/staged release) or it can be released to all users all at once. 

Just because you finished with testing does not mean that your job is done. In that period here is what you need to do:

- Check Crashlytics daily for a week or two for crash issues. 
- Take a look at reviews on its respective stores.

#### Huston, we have a... crash
 
Stop the phased/staged release in case of crash spikes, in that case, a team needs to work on a hotfix build and the whole prerelease process needs to be repeated.

### Google Play Beta/TestFlight - Optional

Are used so that limited (invited) users can test applications in the production environment. 

Once the app is available for installation on Google Play Beta/TestFlight you need to do the following:

1. Make sure that you are added as a beta tester on Google Play Beta or that you are invited to TestFlight. (You will need to install and login into TestFlight on your mobile device) 
2. Install the current store build from the App Store or Google play store. 
3. Set it up and update it with the new Google Play Beta/Testflight build.
4. Do a limited regression test on production to check the most important flows and functionalities.

## Web Apps

Since most of the things that are mentioned in the Mobile Apps part are applicable for Web Apps there is no need to write it all again but we will mention only differences. 

### Choose browsers

- Make sure that you find out which browsers are supported on your app.
- Choose the two most used browsers. First should be your main testing browser, and on a second you should do a limited regression test paying attention to browser differences. 
If there is a time you can do a limited regression test on other supported browsers. 

### Not applicable for Web Apps:

- No need for testing [Prince of Versions](https://infinum.com/handbook/books/qa/testing/testing-prince-of-versions)
- No need for testing Google Play Beta/Testflight 

---

![dilbert-user.gif](/img/dilbert-user.gif)
