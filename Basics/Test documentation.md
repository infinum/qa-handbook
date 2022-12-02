 > Quality needs to be constantly improved, but it is just as necessary to make sure that quality never deteriorates. - Shigeru Mizuno

## Test case

Test case is a group of input values, execution preconditions, expected execution postconditions, and results. We use test cases for creating test executions (smoke test or regression test) and we use those test executions for going through the application (usually before release) and checking if everything is working as expected.

More about writing and maintaining test cases can be read [here](https://infinum.com/handbook/qa/basics/writing-test-cases).


## Test plan

A test plan is a complete planning document that contains the scope, approach, resources, schedule, devices, etc. of testing activities. It helps us determine the effort needed to validate the quality of the application under test - we usually create a test plan for regression and smoke testing which is done before the app goes to production.

The test plan should be created for every release of your application. Also, if you are the only QA on your project, it's still good to have a test plan. By creating a test plan, you will have all the information about testing in one place. Also, other members of your project can understand the details of testing.

Making a test plan document has many benefits:

- Helps people outside the test team such as developers, business managers, and customers understand the details of testing.

- Test plan guides our thinking. It is like a rule book, which needs to be followed.

- Important aspects like test estimation, test scope, and test strategy are documented in the test plan, so it can be reviewed by the management team and re-used for other projects.

- Reminder of a scope that has been covered in the previous test run. The idea is to change the test devices on every test run.

The test plan can be made on Confluence (if you use JIRA for your project) or you can use [this template](https://docs.google.com/spreadsheets/d/1dloUoYvjowlIzo78MvoIg1k5PuOigW9OS_cmHVodPoI/edit#gid=0). **Make sure to first duplicate the sheet before making any changes!**


Important things that the test plan should have:

- **Timeframe**
  - start and end date for your planned testing
  - some important dates for release (code freeze, submission date, release date, etc.)
- **Scope of testing**
  - Example: smoke, full, reduced, etc.
- **Some specific things for your app**
  - Example: test the app in different languages, test as users in different countries, test as users with different roles, etc.
- **Test devices**
  - Write down all devices you will be testing on (device model, OS version, any other specifics that you need).
- **Responsible tester**
  - If you have more than one QA member on your team, write down who is responsible for running each test execution.
- **When**
  - Write down the date/day/week when you plan to run the test execution.
- **Test execution link**
  - Paste the link to your test execution/test run (Jira link or TestRail link)

<span style="display:block; border: 1px solid #e0e0e0; margin-left:auto; margin-right:auto; width:100%;">![JIRA_test_plan.jpg](/img/JIRA_test_plan.jpg)</span>

### Maintaining the test plan:

Maintaining the test plan means that it can be edited and adjusted for every purpose/objective of the project, depending on the scope of the release and the manageable time period.

For every release on the project, it is important to create a new test plan with all the necessary information on how the test run will be done. This also means that if something is changed before the release (scope, devices, etc.), the test plan must be updated as soon as possible so it is up to date.

The current practice that we use at Infinum is that we create and prepare a template that is later used for every release of the application itself. As mentioned before - depending on the scope of the release and the time period that is given to the tester.

  
## Test report

A test report is an organized summary of testing objectives, activities, and results. It is created and used to help stakeholders (product manager, analysts, testing team, and developers) understand product quality and decide whether a product, feature, or defect resolution is on track for release.

A very basic test report for a small application or organization should include, at least, the following:

- Executive Overview - Summary of key findings
- Test Objective - Information about test type and purpose
- Test Summary - Defining passed, failed, and blocked test cases
- Defects - Described with priority and status
   
Every time when a test run is finished and the whole test plan is fulfilled, a tester should generate a test report that is later shared with the whole development team and the stakeholders (clients).

This report can be exported as a PDF file and then sent via e-mail, Slack, or shared via a TestRail link.

### How to generate a test report from TestRail

There are several different test reports you can generate. Here's how you can generate the two most used ones.

**Run summary**

1. Navigate to a test run
2. Click on Run > Summary
3. Click on Add report
4. Wait for it to generate
5. Download it 

**Detailed test report**

1. Navigate to a test run
2. Click on the Print icon
3. Select "Details" from the top dropdown
4. Click on Print and save it as a PDF

<span style="display:block; border: 1px solid #e0e0e0; margin-left:auto; margin-right:auto; width:65%;">![Testrail_test_report.jpg](/img/Testrail_test_report.jpg)</span>

### How to generate a test report from Xray 

1. Navigate to a Test Runs List
2. In the filters dropdown, specify the test plan from which you want to export the executions 
3. In the "Contains" field, add the name of the execution that you will be exporting (sometimes Xray won't return any results so you can try with a couple of key words from your execution's name) 
4. Click "Generate report"
5. On the right side, specify which columns you want to export (this selection should be enough: Key, Summary, Components, Test execution, Test plan, TestRun Status, Test execution fix version, Open, Closed)
6. Export
7. Convert exported file to PDF (open with Numbers and export as PDF)

<span style="display:block; border: 1px solid #e0e0e0; margin-left:auto; margin-right:auto; width:100%;">![Xray_test_report.jpg](/img/Xray_test_report.jpg)</span>

## Test strategy

Test strategy is all the above and extra. Basically, a test strategy is all the documents that explain how the QA process will look like on the specific project. We can also call it a "way of working" for a QA member.

Test strategy documents can contain some information about:

- Scope and overview of the test runs
- Test approach - roles and responsibilities of each team member, type of testing, use of automation tools, etc.
- Test environment - information about different testing environments used in the testing process
- Tools being used on the project - here, we can define the different tools used for different types of operations (test management tools, tools for automation testing, performance testing, etc.)
- Release plan - how and when the release of the application is tackled
- Bug lifecycle - a document that explains the flow of the reported bug (tags, assignees, report location, bug report template)
