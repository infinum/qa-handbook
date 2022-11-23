# Testing activities and artifacts: basics

![Testing artifacts](/img/artifact1.png)

Test artifacts are by-products (outcomes in the image above) of testing activities. Any product/document that was created for testing purposes could be considered a test artifact: plans, strategies, reports, etc.

## Test scenario

A test scenario is like a high-level test case, a single statement that answers the question:
**What to test?**
Each requirement can produce many scenarios, and the goal is to identify as many as possible. Testing scenarios don't require details, so they can come in handy as test reminders when the project is very time-limited.

Imagine testing a photo editing app. One of the requirements would certainly be the image upload. Here are a couple of scenarios that can be derived from this requirement.

**Test scenarios examples**:

- Uploading different file-size images
- Uploading different file extensions
- Uploading by drag and drop
- Multiple photo upload
- Deleting photos
- Uploading photos with identical name

When thinking of test scenarios, don't forget to consider edge cases - investigate how the application works when you go off-script, validate the app's behavior when you don't follow the planned path.

## Test case

After identifying as many scenarios as possible, the next step is defining how to perform them step-by-step.

Test cases are the set of positive and negative executable steps of a test scenario. They answer the question: **How to test it?**

### How to write test cases

This is the minimum information each test case should have:

- Title
- Steps
- Expected result

Additionally, it may also contain:

- Reference (to a requirement, task or user story)
- Prerequisites or pre-conditions (e.g., user role)

Example:

**Title**: Verify that photos can be exported with visible tags

**Pre-conditions**:

The user is logged into his account.

The user has uploaded photos on his account.

**Steps:**

1. Go to the Photos tab
2. Click on the "View photo" button
3. Click on the "Edit tags" button
4. Add tags
5. Click on the "Save tags" button
6. Click on the vertical ellipsis (⋮) in the upper right corner
7. Click on "Download"
8. Click on the "Export with VISIBLE tags" button

**Expected result:**

Verify that all the tags are visible on the exported photo.

**Reference:** (insert link)

These are some basic criteria that your test case should fulfill. It should:

- Reflect how the app should actually behave.
- Be self-contained.
- Check one thing.

You should write both positive and negative test cases.

- Positive test cases test the happy flow - "test to pass".
- Negative test cases test error handling - "test to fail".

You can find more info on negative testing [here](https://infinum.com/blog/negative-scenarios-in-software-testing-best-practices/).

## Test cases: best practices

### Title

The title should clearly state what you are testing. Possible ways to format your title are the following:

- Verify that SOME CONDITION results in SOME RESULT
- Feature should have SOME RESULT when SOME CONDITION


The title should also:

- Use only English.
- Be meaningful and concise (avoid unnecessary words).
- Avoid slang and unclear abbreviations.

Examples:

❌Title 1: Verify that the new Profile is applied by pressing the Choose from profile button, selecting a Profile from the list, and pressing Choose button

✅Title 2: Verify the new profile can be applied

❌Title 3: Type in 123456 in the password field that has Password hint

✅Title 4: Type in an invalid password

### Pre-conditions

Use pre-conditions to avoid repeating steps.

```
Pre-conditions:

The user is logged into his account.
The user has uploaded photos on his account.
```

If we don't use pre-conditions, every test case should start with opening the app, registration, login etc.

**Pre-condition:** The user is on the home screen.

By indicating the user's position in the app, the steps that led him there are known from the previous test cases.

In some tools (Xray in this case), you can create a pre-condition as an issue type, which increases interconnectivity with other issue types. In other words, you can see all the test cases that have that precondition by clicking on it.

![Pre-conditions](/img/artifact4.png)

### Steps and expected behavior

The test case must specify the expected behavior. There is no need to write the expected result for every step, but the last one should always have it. In the expected result, use a form that highlights what the expected result IS, not what it SHOULD BE.

One step should be an atomic one, meaning there should not be any further sub-steps. Try not to have too many steps in a single test case. There is no limit, but when you come to about 15 steps, think again if maybe this test case could be separated into two or even more.

If you struggle with UI terminology, [Material design](https://material.io/components?platform=web) might help.

❌
| Steps | Expected behaviour |
| -------- | -------- |
| 1. Select one photo ~~and tap the delete button~~     | A photo ~~should be~~ deleted.   |


✅
| Steps | Expected behaviour |
| -------- | -------- |
| 1. Select one photo         |   The delete button is displayed.       |
| 2. Tap the delete button   | The photo is deleted.|

❌

| Steps | Expected behaviour |
| -------- | -------- |
| 1. Select one of the items in the dropdown menu    | ~~If~~ the user selects "Other", a text field appears. F~~or any other answer~~, the user can go to the next question.   |

✅

| Steps | Expected behaviour |
| -------- | -------- |
| 1. Select anything but "Other" from the dropdown menu         |       An answer is selected.   |
| 2. Change the answer to the previous question to "Other"   | A text field is displayed.|

### Test data

There is no need to write test cases that check UI. You can add a link to a design page as an expected result of a single step or paste it into the test data field.

![Test case example 1](/img/artifact5.png)

![test case example 2](/img/artifact6.png)

### Test case details

You can choose priority levels that suit your test cases (if needed), and add labels (e.g., smoke_test, login_feature). Labeling is pretty convenient for adding extra info to our test cases and consequently improving their categorization and classification.

![Test case details](/img/artifact7.png)


### Traceability

Test cases should be traceable. Traceability is gained by linking test cases to requirements, user stories or tasks. Test traceability proves that the application functions as expected and ensures effortless access to the original task/requirement. When testing a feature on any project, we should avoid closing the task without providing a connection to the test cases we created or used.

### SMART test cases

Read up on how to make your test cases [SMART](https://www.linkedin.com/pulse/smart-test-cases-kevin-pyles/):

- Shareable
- Manageable
- Adaptable
- Reusable
- Tiered

## How to maintain test cases

![Maintaining test cases](/img/artifact2.png)

Each time you approach a new user story or feature task, write test cases for it. Also, if you find a severe bug, cover that scenario with test cases.

If a task changes some existing behavior, update the old test cases as well. In that way, you'll always have a set of test cases that actually reflect the app.

User stories that simply adjust an image, color scheme or text can be tested only once so these changes don't need to be covered with test cases.


## Test suite and test repository

![Test repository](/img/artifact3.png)

Both the test suite and test repository are collections of test cases. The difference is that the test repository is a collection of all the test cases, and test suite not necessarily.

If you're working on a project with one product, you need only one storage for your test cases. In Jira that is a test repository, and in Testrail you need to choose "Single repository" project type and then you place all your test cases in one suite.

Divide your suite/repository into logical sections. One of the best practices is to divide it into **features** or **screens**.

Test suites and repositories are not test artifacts because they are storage for documents, they are not documents themselves.


### Versioning test suites

If you are working on several app versions at the same time or on projects with multiple products, a good idea is to branch off your current test suite and start maintaining a new one.

At some point in time, you'll have fresh test cases in the new suite that will not interfere with testing the current version.

Once the current version becomes deprecated, you can simply discard the old one.

## Test run/execution

A test run or a test execution is the process of running tests, following your test cases step-by-step and live performing them on the software.

Reasons to start a test execution could be many:

- Functional testing (to verify a new functionality)
- Smoke testing (after a hotfix)
- Regression testing (before release)

The goal of all these testing activities is to find out whether the software works as it is supposed to. If the test execution returns the expected results, the test passes. Contrarily, if the expected result does not match, the test fails. In case of a failure, a bug report must be created.

Once the execution is done, you can generate a report with all the info about your test results.

Analogous to repository, test runs are not artifacts, but the reports they generate are test artifacts.