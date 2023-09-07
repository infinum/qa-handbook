There are various test case management tools out there. We came to use Gurock Software's Testrail.

Read up on it [here](https://www.gurock.com/testrail/docs/user-guide). 

## What is a test suite?

- A test suite is a set of test cases.
- A test suite may be divided into sections.
- A test case is one test you can execute manually.

Each project can have several test suites and the scope of the test suite may vary. You might want to test *everything*, or just assemble a test suite that will be used for sanity checks.

Divide your test suite into digestible sections. One of the best practices is to divide it into features or screens, depending on the type of project you are working on.

## How to quickly write & import test cases

You could find yourself caught in one of the following scenarios:

- You start working on a project that has no test documentation at all.
- You have very limited time to work on test documentation.
- You already have test documentation in XLSX or CSV and you want to import it into Testrail for easier usage.

If that is the case, there is an easy way to quickly get yourself up and running:

- Sketch out your test cases in XLSX/CSV

![tr1.png](/img/tr1.png)

- Navigate to your Testrail project
- Click on "Import Cases" and select your file
- Map your columns to Testrail fields

![tr1.png](/img/tr2.png)

- Import them and voilà...

![tr1.png](/img/tr3.png)

You will quickly and easily get a structure you can build on and immediately start executing tests.

N.B., if your file does not contain one test case per row, check out the [official user guide](https://www.gurock.com/testrail/docs/user-guide/howto/import-csv).

## How to maintain test cases

- Each time you approach a new task, write test cases for it.
- If it changes some existing behaviour, update the old test cases as well. In that way, you'll always have a set of test cases that actually reflect the app.

## Versioning test suites

If you are working on several app versions at the same time, a good idea is to branch off your current test suite and start maintaining a new one.

At some point in time, you'll have fresh test cases in the new suite that will not interfere with testing the current version.

Once the current version becomes deprecated, you can simply discard the old one.

## How to run a test suite

To run a test suite:

1. Navigate to Test Runs & Results
2. Select a test suite
3. Give the test run a name
4. Enter the test device, build, environment and other meta data to the description
5. Exclude some test cases if you agreed to skip them
6. Add the test run
7. Go through each test case and assign it a status (Passed, Blocked, Retest, Failed)
8. Create bugs in your project management tool if you find them and notify the team
9. Once you are done, close the test run
10. Generate a test report

## How to generate test reports

here are several different test reports you can generate, here's how you can generate two most used ones.

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