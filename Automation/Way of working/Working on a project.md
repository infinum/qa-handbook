## Working on a project

When working on a project with multiple people/teams, you should agree on a _way of work_ and have it written down as soon as possible, preferably during your first days on the project.

This should contain info on the test automation process in SDLC (Software Development Life Cycle), such as:

- requesting and verifying the locators needed for test automation
- when the tests are being run
- which tests are run and on which build/environment
- responsibility for checking the test report and reporting bugs


### Requesting IDs

Ideally, if test automation is being done on the project, you should have most of the locators ready. If not, it is important to discuss early on who will be responsible for:

- preparing the locators (how they should look like and which element to put them on)
- opening tasks for developers requesting new locators
- verifying the locators are put on the correct elements

It will usually be the responsibility of a TAE. In case there are multiple TAEs on the project, a dedicated person should be decided on to make the process faster.

A few things to consider when opening a new task:

- task should be short and concise
- better to open a few smaller ones than one big one
- have the tasks logically structured (e.g. per screen or feature)
- add a link to the design

When preparing the locators, you should consider a tool that is already being used for design. In case the design is being done in Figma, you could use that one. Not to mess up the design, you should create a separate document that will contain all the screens to which you want locators to be added. Simply copy and paste the screens and using tools like an arrow and a text field, mark the element that needs a locator. Then, when opening a task for the developers, insert the link that points to the screen with marked elements.

When working on locators, it would be wise to have a page with a few examples, a "standardization" of a sort. For example, you want all the buttons to be prefixed with "btn\_" or suffixed with "\_button". The same goes for all other elements like input fields, sliders, etc.

Maybe the developers on the project already have an agreed way of working, so you could continue with that. The idea is to have somewhat similar-looking locators throughout the app.

**NOTE:** 
- A "known issue" is when there are multiple child elements inside a parent element. For example, a LayoutView in Android might have multiple elements. Depending on the functionality, you will probably need a separate locator for each of those child elements. Otherwise, if a locator is put on the LayoutView, you will only get a better-looking XPath on the child elements. Think twice when considering elements that need a locator.


## Who writes test cases?

Test cases are developed by person / team that is using them. If (manual) test cases are primarily used by the QA team, then writing and updating them is their responsibility.

You as a TAE can and should help out in test development and maintenance. If labels are used to mark the tests, it is your responsibility to make sure that test cases are correctly labeled.

TAE **should not** ask the QA team to adjust test cases so that they could be automated more easily.
This could lead to QA focusing too much on writing the appropriate test for test automation, and not writing a good test that helps in testing.


## Which tests to automate?

This depends on what you decide as a team, and which type of tests you are working on. 
If you are, for instance, working on UI test automation, you most likely will not be able to automate everything, for whatever reason.

In any case, make sure that your code is readable and that the tests are stable. 
It is not how many tests there are, but whether are they doing the work they are supposed to do.


## Test reports

One of your tasks is to often check the reports generated by test automation.

If there are tests that ended in error or fail, make sure the issue is not in the framework or a mistake in the tests. If the issue is in the app, report it to the QA team for further investigation.


## Meetings

TAE should attend all the meetings that other team members are attending; daily standup, sprint planning, backlog refinement, sprint review, sprint retrospective, etc.
If there are additional QA syncs, TAE should be present. 

In some cases (if not most) you will work on regression tests and it might seem that attending meetings is a waste of time. However, think again.
Your experience and insights will definitely be valuable to the team. Besides, hearing about what is being developed right now will help you prepare for the upcoming test automation work.