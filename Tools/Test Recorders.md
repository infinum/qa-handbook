> It's automation, not automagic. — Jim Hazen

## What are test recorders?

Test recorders are software tools that are recording steps that testers are doing while manually testing web-based apps. But not just that - they also gather a lot of information regarding properties of elements, input field values, conditions, validations, and much more, depending on the tool you use.

Once the steps are recorded, by pressing the start button the test will repeat itself with the exact steps the tester previously made. The great thing about it is that steps can be modified based on various parameters that you would need in future test runs.

## When to use test recorders?

The best use cases for test recorders are tests that require a lot of step repetition over and over again. Besides that, tests have to be bullet-proof on all supported browsers.

Test recorders are great for all manual testers and even better for someone who is considering doing test automation on a daily basis. These tools will surely help you to think like a test automation engineer because there are many things to consider 
when you create tests this way. To be future-proof, the use of some advanced options for validation like locators, waits, breakpoints, and others will be a must.

## Testim introduction

Testim is a testing platform that uses AI for authoring, execution, and maintenance of automated tests. It offers great integration with various services and apps:

- **Git integration** - always up to date with the latest code version
- **Apps and services** - Slack, Browserstack, TestRail
- **Run test with CLI** - CI (i.e. Jenkins, CircleCI, Azure pipelines…) or local on your browser, also there is *testim grid* with grid management (run tests on all well-known browsers at once)
- **Testim REST API** - you can do actions with branches (create, merge, and others), retrieve and run tests
- **Labs** - better organization of tasks (visual, webhook integration for notifications)💰
- **Bug tracker** - Jira, Slack, Trello, GitHub
- **Report** - weekly email report💰 

![test_recorders1](/img/test_recorders1.png)

After the test is successfully recorded all the steps will be shown in a grid on a very user-friendly UI.

<span style="display:block; border: 1px solid #e0e0e0;">![test_recorders2](/img/test_recorders2.png)</span>

### Some key features of Testim:

- **Element lock-in** - automatically detecting locators without user action
- **Steps share** - steps or groups of tests can be reused across different tests 

<span style="display:block; border: 1px solid #e0e0e0;">![test_recorders3](/img/test_recorders3.png)</span>

- **Visual configuration** - reordering, deleting, skipping steps based on the scenario of the test itself
- **Customizable with code** - insert custom JavaScript code (i.e. for clearing cookies or something different) with a real JS editor


![test_recorders4](/img/test_recorders4.png)

### Real-life testing

This tool was used on one of our projects and the experience from that testing was positive:

- Steps are recorded well - if there was some issue with some individual steps, they were fixed easily because you can start the test from a specific step and skip the problematic ones or disable them for that run
- Since all steps are editable you can also add specific locators, login data, conditions, wait for a condition where you think that it is needed
- Surprisingly, attaching an image from the folder on the local computer to the web page works like a charm - it tracks and records your clicks where you attach the image from your folder on the computer and attaches it the same way
- Running the whole suite with multiple individual tests was also possible in the free version.

## Compared to Selenium IDE

Selenium IDE is a selenium-powered test recorder. In comparison to Selenium IDE, Testim has more AI features integrated with it. Some basic actions are working much better on Testim and it doesn't get confused so easy during test recording (i.e. when the 1Password popup is shown on the login screen, Selenium IDE gets confused sometimes and won't pass that step).

**Differences that are most noticeable between the two are:**

- Selenium IDE is a web extension and Testim is a full web application
- UI/UX is much better on Testim
- More control options for step manipulation and editing in Testim
- Better integration options in Testim that are easy to use and which are not available in Selenium IDE
- Integration options are easier accessible and visible at first sight in Testim, whereas on Selenium IDE you need to dig deeper to find some advanced option
- Better overview of the state of tests, statistics, test suites, and more

<span style="display:block; border: 1px solid #e0e0e0;">![test_recorders5](/img/test_recorders5.png)</span>

For users that are not familiar at all with web testing and elements that you need to adapt or customize, Testim is a much better option even in the free version because Selenium IDE requires some learning curve. Some features in Selenium IDE are not visible or understandable at first sight.
