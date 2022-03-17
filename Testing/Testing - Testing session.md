
## Introduction

The testing session is an event you can integrate into your process of releasing a mobile or a web app. The idea is to create a meeting with colleagues from the project you are working on and test as a group. You can invite all team members - developers, designers, testers, and your project manager. If the clients are up for it, you can invite them as well.

Testers execute regression tests on most projects to check if everything works as expected before the production release. Test docs are often used to guide those regression tests. Testing sessions are not meant to replace those scripted regression tests, they are a supplementary process.

## Benefits of testing sessions

There are a lot of benefits to organizing a testing session with your project team:

-   Since every project member gets involved in the testing process, they are introduced to parts of the system they don't know well. For example, it's a great way for a backend developer to become more familiar with the frontend.
-   The testing session is a great way to find a lot of bugs in a short period.
-   Since testing sessions are collaborative, they help project members become closer and improve the team spirit.
-   Adding additional pairs of eyes helps find lots of issues fast.
    

## Basic steps

1.  Explain the purpose and benefits of a testing session with your project team.
    
2.  Create a calendar event for the testing session.
    
3.  Prepare a test plan.
    
4.  Make a small introduction for the app/features that will be tested.
    
5.  Test the app during the testing session.
    
6.  Collect all the issues that were found and open tasks in your project management tool.
    

## What is your role?

A tester that organizes the testing session event is also a moderator. Make sure to:

-   Prepare everything that is needed for the testing session. That includes the test plan, test devices, and access to various browsers or Browserstack.
-   Manage the session and help participants in case they get stuck or need some guidance during testing.
    

## Creating a test plan

The organizer should create a test plan for all the participants of the testing session.

  

A good practice is to divide the application by features or specific parts which need to be tested and then allocate every part to a participant of the testing session. The test plan should include:

-   General information and preconditions: build, link to the design (Figma, Zeplin), link to the page, etc.
-   Test plan for each of the participants: list of modules/features to test, which device/browser to use.
-   A place where they can report bugs that they find.
    

Later on, when the time is up and the bugs you all found are on the list, the moderator should create a task for every bug in the project management tool (Productive, Jira, etc.).

You can find the template for the testing session [here](https://docs.google.com/spreadsheets/u/0/d/1-K0ruKggRnxOOEhLa_vrt8yjDWaxHQZO9QvCtuIlpPo/edit). Feel free to copy it and use it for your project. Also, check out the [test plan](https://docs.google.com/spreadsheets/d/1GOo7AQgINTd7XOby0wry0H9fdRURbqoOUaTTA-TPrMQ/edit?usp=sharing) that was used for a testing session on the Modra  project.

## General tips for the testing session

-   A testing session event should usually last for 2-3 hours. It can be divided into more sessions depending on the number of features being tested. Of course, it also depends on how much time your participants have at their disposal.
-   When possible, create a friendly and comfy environment. For example, bring sweets and drinks. You can even play some quiet music.
-   In case of duplicates, make sure to merge all the issues before reporting them into your project management tool. Don’t bother organizing them during the session itself.    
-   If the testing session is hybrid, make sure that everyone has at least one device for testing and try to include them in the conversation. Using webcams and sharing your screen can help.   
-   Testing is usually done on a non-production environment which needs to be as similar as possible to the production environment. If there is no production environment, make sure that no changes are being deployed to your chosen environment while the testing session is under way.
