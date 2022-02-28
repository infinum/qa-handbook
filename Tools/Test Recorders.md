## What are test recorders?

Test recorders are software tools that are recording steps that testers are doing while manually testing web-based apps, 
but not just that it also gathers a lot more information regarding properties of the elements, input fields values, 
conditions, validations, and much more, depending on the tool you use.

Once the steps are recorded, by pressing the start button test will repeat itself with exact steps testers 
previously made, but the great thing about it is that steps can be modified based on various parameters that you would 
need in the future test runs.

## When to use test recorders

The best use cases for test recorders are tests that require a lot of steps over and over again. Besides that, 
they have to be bullet-proof on all supported browsers.

Test recorders are great for all manual testers and even better for someone that is considering doing automation daily 
and these tools will surely help you to think like the automation tester because there are much more things to consider 
when you create tests this way. To be future-proof, the use of some advanced options for validation like 
locators, waits, breakpoints, and others will be a must.

## Testim introduction

Great integration with all known services and apps:

- **Git integration** - always up to date with the latest code version
- **Apps and services** - Slack, Browserstack, TestRail
- **Run test with CLI** - CI (i.e. Jenkins, Circle CI, Azure pipelines…) or local on your browser, also there is
_testim_ grid with grid management (run tests on all well-known browsers at once)
- **Testim REST API** - where you can do actions with branches (create, merge, and others)
- **Labs** - better organization of the tasks (visual, webhook integration for notifications)💰
- **Bug tracker** - Jira, Slack, Trello, Github
- **Report** - weekly email report💰 

![test_recorders1](/img/test_recorders1.png)

After the test is successfully recorded all the steps will be shown in a grid on a very user-friendly UI.

![test_recorders2](/img/test_recorders2.png)

### Some key features of Testim:

- Element lock-in - automatically detecting locators without user action
- Steps share - steps or groups of tests can be reused across different tests 

![test_recorders3](/img/test_recorders3.png)

- Visual configuration - reordering, deleting, skipping steps based on the scenario of the test itself
- Customizable with code - insert custom JavaScript code (i.e. for clearing cookies or something different) 
with a real JS editor


![test_recorders4](/img/test_recorders4.png)

### Real-life testing

This tool was used on one of our projects and experience form that testing was positive:

- Steps are recorded well if there was some issue with some individual steps that were fixed easily because 
you can start the test from a specific step and problematic one skip or disable for that run
- Since all steps are editable you can also add specific locators, login data, conditions, wait for a condition 
where you think is much needed
- Surprisingly attaching an image from the folder on the local computer to the web page works like a charm, 
it just follows your clicks where you attach the image from your folder on the computer and attach it the same way

Running the whole suite with multiple individual tests was possible also in the free version.

## Compared to Selenium IDE

Selenium IDE is a selenium-powered test recorded the same as Testim, but Testim has more AI features integrated with it.
Some basic actions are working much better and it is not so easy to get confused during test recording 
(i.e. when 1Password popup is shown on the login screen, Selenium IDE gets confused sometimes and won&#39;t pass that step)

**Differences that are most noticeable between the two are:**

- Selenium IDE is a web extension and Testim is a full web application
- UI is much better on Testim
- Much more control options for steps manipulation, editing
- Better integration options that are easy to a user inside the Testim UI that are not available on Selenium IDE
- Integration is much more accessible at first sight on Testim, on Selenium IDE you need to dig deeper to find some 
advanced option

- Better overview of the state of the tests, statistics, test suites, and more

![test_recorders5](/img/test_recorders5.png)

For users that are not familiar at all with web testing and elements that you need to adapt or customize, Testim is a much better option even in the free version because Selenium IDE requires some learning curve. Some features are not all visible or understandable at first sight.