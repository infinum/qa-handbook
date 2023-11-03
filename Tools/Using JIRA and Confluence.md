>  Let’s go invent tomorrow instead of worrying about what happened yesterday. - Steve Jobs 

## Atlassian JIRA

Jira is an issue tracking, project management, and bug tracking tool that is compatible with agile methodologies for organizing software development.

<span style="display:block; border: 1px solid #e0e0e0; margin-left:auto; margin-right:auto; width:90%;">![ira_article_1](/img/jira_article_1.png)</span>

The product name is a truncation of Gojira, the Japanese word for Godzilla. The name originated from a nickname Atlassian developers used to refer to Bugzilla, which was previously used internally for bug tracking. It's pronounced Jira (/ˈdʒiːrə/ JEE-ra). Source - [Wikipedia](https://en.wikipedia.org/wiki/Jira_(software))

Jira uses different terminology than Productive, let's have a look at of the terms that are used in Jira. 

## Issues 

All work items are called Issues in Jira and are segmented into:

* Epic
* User story 
* Task
* Subtask 
* Bug 

> Quick tip: you can quickly start creating an Issue by pressing “c” on your keyboard or “+” in the Jira sidebar menu.

The main difference that could cause confusion and raised eyebrows when switching from Productive to JIRA is that tasks are now Issues! All other terminology is the same.

### Issue types & priority

* **Epic >** is usually a collection of user stories
* **User story >** is the smallest unit of work in an agile framework expressed from the software user's perspective
* **Task	>** represents work that needs to be done
* **Sub-task >** is a piece of work that is required for a task
* **Bug >** is a problem that impairs or prevents the functions of a product

For every issue, there is a priority that can be set

* **Highest >** Indicates that this issue takes precedence over all others
* **High >**	Indicates that this issue is causing a problem and requires urgent attention
* **Medium >** Indicates that this issue has a significant impact
* **Low	>** Indicates that this issue has a relatively minor impact
* **Lowest >** Lowest priority

### Creating a new Issue

You can create a new Issue in two ways - by clicking on the "create" button or directly in the board view by clicking on the + icon.

#### Examples
  
<span style="display:block; border: 1px solid #e0e0e0; margin-left:auto; margin-right:auto; width:90%;">![ira_article_2](/img/jira_article_2.png)</span>

<span style="display:block; border: 1px solid #e0e0e0; margin-left:auto; margin-right:auto; width:90%;">![ira_article_3](/img/jira_article_3.png)</span>


> All Issues have a status they can be set to. Issue statuses can be configured per projects. For example, let's use this project board: 

<span style="display:block; border: 1px solid #e0e0e0; margin-left:auto; margin-right:auto; width:90%;">![ira_article_4](/img/jira_article_4.png)</span>

> Every project board is configured differently, most of the time special fields in the new Issue creator will have sprint and fix version fields. 

**Sprint** — *also known as an iteration* — is used to determine which current sprint issue is tied to. It is a short period in which the development team implements and delivers a discrete and potentially shippable application increment, e.g. a working milestone version. 

**Fix version** - field is used for the version you plan on releasing with a feature or bugfix to production. 

 Mostly used for;

* release planning
* monitoring progress and velocity
* reporting

<span style="display:block; border: 1px solid #e0e0e0; margin-left:auto; margin-right:auto; width:90%;">![ira_article_5](/img/jira_article_5.png)</span>

## Backlog
The backlog is the global "to-do list" for upcoming releases. A backlog is usually composed of three key hierarchical pieces:

* **Initiatives** - Higher-level business priorities or big projects potentially spanning multiple teams
* **Epics** - Once the higher-level priorities are settled, the initiatives break down into large pieces of work, which consist of multiple stories
* **Stories** - User stories capture functionality requirements

## Active sprint 

The Active sprints display the issues that the team is currently working on. You can create and update Issues, and drag and drop them to transition them through a workflow in the scrum board.

> How the new sprint is created: 
> 
> 1. From your project’s sidebar, select your Backlog.
> 2. Click Create sprint at the top of the backlog section. The new sprint will appear below the current sprint.
> 3. Select add dates (located under the sprint’s header) to plan the start and end date of your future sprint.

## Your work 

This is the part of Jira where all you ever worked on is being documented, here you can find things you worked on, things you viewed on the project, everything that was assigned to you, and things you have marked with a star.

> To access **"your work"** just click on it on the top tray menu of the JIRA. 
> 
> <span style="display:block; border: 1px solid #e0e0e0;">![ira_article_6](/img/jira_article_6.png)</span>

## Reports
Reports give you a graphical overview of the different aspects of your plan.

The most important ones for us are the **burndown chart** and the **velocity chart**.

### Burndown chart

A burndown chart shows the amount of work that has been completed in an epic or sprint, and the total work remaining. Burndown charts are used to predict the team's likelihood of completing their work in the time available.

> Burndown charts are useful because they provide insight into how the team works. For example:
> 
> * If the team consistently finishes work early, this might be a sign that they aren't committing to enough work during sprint planning. 
> 
> * If the team consistently misses their forecast, this might be a sign that they've committed to too much work.
>  
> * If the burndown chart shows a sharp drop during the sprint, this might be a sign that work has not been estimated accurately, or broken down properly.

### Velocity chart

The velocity chart shows the amount of value delivered in each sprint, enabling the team to predict the amount of work they can get done in future sprints. It is useful during sprint planning meetings, to help decide how much work can feasibly be committed to.

**Viewing the Velocity Chart**

1. Navigate to your desired board.
1. Click Reports, then select Velocity Chart.
1. The Velocity Chart will be displayed, showing your last seven completed sprints.

> Quick tip: Click **How to read this chart** at the top of the report to view a short description of the report in JIRA.

### Filtering and JQL

JIRA board's filter is an issue filter (a JQL query) that specifies which issues are included on the board. For example, the board may include issues from multiple projects, or only one project, or a particular component of a project.

> JQL stands for Jira Query Language and is the most powerful and flexible way to search for your issues in Jira. JQL is for everyone: developers, testers, project managers, and business users.


Since filtering is rather complex, refer [to this link](https://support.atlassian.com/jira-software-cloud/docs/configure-filters/) for more information on how to configure filtures, and [this link](https://www.atlassian.com/blog/jira-software/jql-the-most-flexible-way-to-search-jira-14) for more details on JQL itself.

## Releases and versions

Releases represent points in time for the project. They can be used to schedule how features are rolled out to users, or as a way to organize work that has been completed for the project.

> In Jira Software, each release is called a version! A version is a set of features and fixes released together as a single update to your product. 

Assigning issues to versions help to plan the order in which new features (stories) for the application will be released to users. In Jira, you can view issues according to which version they belong to. This helps plan upcoming versions of the application, which may span multiple sprints.

## Boards

Boards simply display all active work items. 

You'll probably spend most of your time looking at the active sprint: 

<span style="display:block; border: 1px solid #e0e0e0; margin-left:auto; margin-right:auto; width:90%;">![ira_article_7](/img/jira_article_7.png)</span>


## Confluence


Confluence is a team workspace in which the team can create, capture, and collaborate on ideas for the project. It helps the team to structure, organize, and share work, so every member has visibility into knowledge and access to the information they need regarding the project.

> **Confluence is organized into spaces.** Spaces are collections of related pages that the team can work on together. Most organizations use a mix of team spaces and software project spaces:
> 
> * Team spaces - team members use it to work together toward large-scale goals and OKRs. 
> 
> * Software spaces - for keeping track of individual initiatives and projects. 
> 
> * Documentation spaces - teams use it to create and organize technical documentation for products and services, so it’s easy for anyone to use.
> 
> * Knowledge spaces - for storing answers to common questions, such as policy clarifications and IT solutions. 

Personal space is mostly used as a sandbox to organize your notes, keep track of personal OKRs and goals.

Confluence and Jira complement each other. Confluence is used for storing thoughts, plans, and knowledge of the team, while Jira is used to track issues and organize work.

## Xray

Xray is a Test Management tool that provides the structure to plan, organize, and report on the progress of testing as well as the readiness to deploy.

It enhances agile boards by tracking the requirement status and test execution progress in real-time. Using Xporter you can generate advanced reports that can be exported to docx, xlsx, or pdf.

### Basic Xray concepts

**TEST CASE**

* A single unique scenario to be tested.

**TEST REPOSITORY**

* Collection of all Test Cases.
* There is only one Test Repository.
* Test Cases within it can be grouped into folders.
* Test Cases should be unique.

**TEST SET**

* A collection of Test Cases.
* Multiple Test Sets can be created.
* One Test Case can be in multiple test sets.
* You will usually use either Test Sets or the Test Repository to organize your Test Cases, not both.

**TEST PLAN**

* A collection of Test Cases or Test Sets that will be tested.
* Multiple Test Plans can be created.

**TEST EXECUTION**

* A collection of Test Cases, Test Sets, or Test Plans.
* Each Test Case becomes executable.
* Each Test Case within it has a pass/fail/progress status.

## Creating a new test case 

To create a new test issue follow these steps: 

**Step 1**: Click Create Issue at the top of the screen to open the Create Issue dialog box/page.

<span style="display:block; margin-left:auto; margin-right:auto; width:80%;">![ira_article_8](/img/jira_article_8.png)</span>

**Step 2**: Select the Project. On Issue Type, select Test.

**Step 3**: Type a Summary for the test and fill at least all mandatory fields marked with an asterisk.

<span style="display:block; margin-left:auto; margin-right:auto; width:80%;">![ira_article_9](/img/jira_article_9.png)</span>

**Step 4**: When you are satisfied with the content of your test, click the Create button

> There you have it, your very own first test in Xray. For in-depth information about Xray and JIRA test integration you can [follow this link](https://www.atlassian.com/devops/testing-tutorials/jira-xray-integration-manage-test-cases).

## Additional resources

- [Free Xray courses](https://academy.getxray.app/catalog/index)



## Zephyr Scale

Zephyr Scale is a versatile test management tool that can adapt to different development and testing methodologies, including both traditional (Waterfall) and Agile approaches. Its integration with Jira makes it particularly suitable for Agile teams, while its comprehensive test case management features benefit projects following Waterfall or other structured methodologies.


### Core features and concepts

**Test library**
The Test Library is where you create, store, and organize your testing artifacts, including test cases, test cycles, and test plans. It serves as the central repository for all your testing needs, ensuring that your testing assets are well-structured and accessible. 

**Test cases**
Test cases are created in Test library, in the Test cases view.
![Test library: Test cases view](/img/zephyr_test_library.png)

They can be assigned to individual tester.
![Create Test Case : Details tab](/img/zephyr_test_case_details.png)

You can create detailed test scripts with step-by-step instructions, making it suitable for both traditional and Behavior-Driven Development (BDD) approaches. Additionally, plain text scripts are supported for simplicity.

![Create Test Case: Test Script tab](/img/zephyr_test_script.png)


**Call to test**
When crafting test cases, Zephyr Scale allows you to import another test case as a step. This feature, known as 'Call to Test', streamlines your test case creation process by embedding all the steps from the referenced test case into the new one. It promotes reusability and reduces duplication of steps.

![Call to test](/img/zephyr_call_to_test.jpeg)

**Version control**
Version control is another essential feature in Zephyr Scale. You can create multiple versions of a test case, each representing a distinct instance of that test. This versioning capability aids in tracking changes and ensures that historical test cases remain accessible. When running a test case, you have the flexibility to select the specific version you want to execute, enhancing test case management.

![Version control](/img/zephyr_version control.png)

**Traceability**
Linking test artifacts to Requirements. When you create or edit any test artifact (test plan, test cycle, test case) in Zephyr Scale, you can associate it with specific requirements or user stories. 
![Test case: Traceability](/img/zephyr_traceability.png)

**Test cycles**
Test cycles are collections of test cases organized to achieve specific testing objectives. They can be assigned to individual testers and associated with particular testing environments. Additionally, test cycles provide real-time insights by comparing estimated progress with actual results. This feature enhances test planning and execution efficiency.

![Test library: Test Cycles view](/img/zephyr_test_cycles.jpeg)

**Reports**
Verious test report are easily generated and customizable. They can be tailored to meet specific project requirements. These reports offer valuable insights, aiding in the identification of key metrics, tracking testing progress, identifying defects, and supporting informed decision-making.
![Reports](/img/zephyr_test_reports.png)


**Additional resources**
* [Zephyr Scale documentation](https://support.smartbear.com/zephyr-scale-server/docs/welcome.html)



