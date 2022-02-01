>  Let’s go invent tomorrow instead of worrying about what happened yesterday. - Steve Jobs 

## Atlassian JIRA

Is an issue tracking, project management, and bug tracking tool that allows agile framework for management. 

![](/Users/dfazlic/Documents/JIRA članak slike /Slika 1.png)

The product name is a truncation of Gojira, the Japanese word for Godzilla. The name originated from a nickname Atlassian developers used to refer to Bugzilla, which was previously used internally for bug-tracking. It's pronounced Jira (/ˈdʒiːrə/ JEE-ra). Source - [Wikipedia](https://en.wikipedia.org/wiki/Jira_(software))

JIRA uses different terminology than Productive, let's see some of the terms that are used in JIRA. 

## Issues 

All work items are called Issues in Jira and are segmented into:

* Epic
* User story 
* Task
* Subtask 
* Bug 

> Quick tip: you can quickly start creating an Issue by pressing “c” on your keyboard or “+” in the Jira sidebar menu

The main difference that could cause confusion and raised eyebrows when coming from Productive to JIRA is that tasks are now Issues!. All other terminology is the same

### Issue types & priority

* **Epic >** is a big user story that needs to be broken down into smaller stories
*  **User story >** is the smallest unit of work that needs to be done
* **Task	>** represents work that needs to be done
* **Sub-task >** is a piece of work that is required for a task
* **Bug >** is a problem that impairs or prevents the functions of a product

For every issue, there is a priority that can be set

* **Highest >** Indicates that this issue takes precedence over all others
* **High >**	Indicates that this issue is causing a problem and requires urgent attention
* **Medium >** Indicates that this issue has a significant impact
* **Low	>** Indicates that this issue has a relatively minor impact
* **Lowest >** Lowest priority



### Creating a new ISSUE

To create a new issue (task) you can do it in two ways clicking on the "create" button in the JIRA topbar or directly in the board view by clicking on the + icon.

> **Examples**:
  
![](/Users/dfazlic/Documents/JIRA članak slike /Slika 2.png)
![](/Users/dfazlic/Documents/JIRA članak slike /Slika 3.png)


> All issues have the status they can be set to, issue statuses depend on the project and how the main board is configured. For example, let's use this project board: 

![](/Users/dfazlic/Documents/JIRA članak slike /Slika 4.png)

> Every project board is configured differently, most of the time special fields in the new issue creator will have sprint and fix version fields. 

**Sprint** — *also known as an iteration* — is used to determine which current sprint issue is tied to. It is a short period in which the development team implements and delivers a discrete and potentially shippable application increment, e.g. a working milestone version. 

**Fix version** - field is used for the version you plan on releasing with a feature or bugfix to production. 

 Mostly used for;

* release planning
* monitoring progress and velocity
* reporting

![](/Users/dfazlic/Documents/JIRA članak slike /Slika 5.png)




## Backlog
The backlog is the global "to-do-list" for the upcoming releases. A backlog is usually composed of three key hierarchical pieces:

* **Initiatives** - Higher-level business priorities or big projects potentially spanning multiple teams
* **Epics** - Once the higher-level priorities are settled, the initiatives break down into large pieces of work, which consist of multiple stories
* **Stories** - User stories capture functionality requirements

## Active sprint 

The Active sprints display the issues that the team is currently working on. You can create and update issues, and drag and drop issues to transition them through a workflow in the scrum board.

> How the new sprint is created: 
> 
> 1. From your project’s sidebar, select your Backlog.
> 2. Click Create sprint at the top of the backlog section. The new sprint will appear below the current sprint.
> 3. Select add dates (located under the sprint’s header) to plan the start and end date of your future sprint.

## Your work 

This is the part of JIRA where all you ever worked on is being documented, here you can find things you worked on, things you viewed on the project, everything that is and was assigned to you, and things you have marked with a star.

> To access **"your work"** just click on it on the top tray menu of the JIRA. 
> 
> ![](/Users/dfazlic/Documents/JIRA članak slike /Slika 6.png)

## Reports
The reports in Portfolio for Jira give you a graphical overview of the different aspects of your plan.

The most important ones for us are **burndown chart** and **velocity chart**.

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

The Velocity Chart shows the amount of value delivered in each sprint, enabling the team to predict the amount of work they can get done in future sprints. It is useful during sprint planning meetings, to help decide how much work can feasibly be committed to.

**Viewing the Velocity Chart**

1. Navigate to your desired board.
1. Click Reports, then select Velocity Chart.
1. The Velocity Chart will be displayed, showing your last seven completed sprints.

> Quick tip: Click **How to read this chart** at the top of the report to view a short description of the report in JIRA.

### Filtering and JQL

JIRA board's filter is an issue filter (a JQL query) that specifies which issues are included on the board. For example, the board may include issues from multiple projects, or only one project, or a particular component of a project.

> JQL stands for Jira Query Language and is the most powerful and flexible way to search for your issues in Jira. JQL is for everyone: developers, testers, project managers, and business users.


Since filtering is rather complex in a way that a lot can be done with it, for detailed instructions please refer [to this link](https://support.atlassian.com/jira-software-cloud/docs/configure-filters/) and for JQL explanation on [this link.](https://www.atlassian.com/blog/jira-software/jql-the-most-flexible-way-to-search-jira-14)

## Releases and versions

Releases represent points in time for the project. They can be used to schedule how features are rolled out to users, or as a way to organize work that has been completed for the project.

> In Jira Software, each release is called a version! A version is a set of features and fixes released together as a single update to your product. 

Assigning issues to versions help to plan the order in which new features (stories) for the application will be released to users. In JIRA, you can view issues according to which version they belong to. This helps plan upcoming versions of the application, which may span multiple sprints.

## Boards

* Boards simply display all active work items 
* The main board: "Your project board" in this case "**TP board**"

The board displays: Active sprint, this is the view you’ll use most of the time spent in JIRA

![](/Users/dfazlic/Documents/JIRA članak slike /Slika 7.png)


## Confluence


Confluence is a team workspace in which the team can create, capture, and collaborate on ideas for the project. It helps the team to structure, organize, and share work, so every member has visibility into knowledge and access to the information they need regarding the project.

> **Confluence site is organized into spaces.** Spaces are collections of related pages that the team can work on together. Most organizations use a mix of team spaces and software project spaces:
> 
> * Team spaces - team members use it to work together toward large-scale goals and OKRs. 
> 
> * Software spaces - for keeping track of individual initiatives and projects. 
> 
> * Documentation spaces - teams use it to create and organize technical documentation for products and services, so it’s easy for anyone to use.
> 
> * Knowledge spaces - for storing answers to common questions, such as policy clarifications and IT solutions. 

Personal space is mostly used as a sandbox to organize your notes, keep track of personal OKRs and goals.

Confluence complements Jira applications and each other. Confluence is used for storing thoughts, plans, and knowledge of the team, and JIRA to track issues.

## Xray

Xray is a Test Management tool that provides the structure to plan, organize, and report on the progress of testing as well as the readiness to deploy.

It enhances agile boards by tracking the requirement status and test execution progress in real-time. Using Xporter you can generate advanced reports that can be exported to Docx, xlsx, or pdf.

### Test process in JIRA with Xray  

Each testing phase allows you to use the following issues:

* **Plan phase**: Test plan issues
* **Design phase**: The specification is defined using precondition and test issue types 
* **Execute phase**: Test execution issues
* **Report phase**: Test execution 

### Basic Xray concepts

**TEST CASE**

* A single unique scenario to be tested.

**TEST REPOSITORY**

* Collection of all Test Cases. There is only one Test Repository
* Test Cases within it can be grouped into folders
* Test Cases should be unique

**TEST SET**

* A collection of Test Cases.
* Multiple Test Sets can be created.
* One Test Case can be in multiple test sets.

**TEST PLAN**

* A collection of Test Cases or Test Sets that will be tested.
* Multiple Test Plans can be created.

**TEST EXECUTION**

* A collection of Test Cases, Test Sets, or Test Plans.
* Each Test Case becomes executable.
* Has a pass/fail/progress status.

## Creating a new test case 

To create a new test issue follow these steps: 

**Step 1**: Click Create Issue at the top of the screen to open the Create Issue dialog box/page.

![](/Users/dfazlic/Documents/JIRA članak slike /Slika 8.png)

**Step 2**: Select the Project. On Issue Type, select Test.

**Step 3**: Type a Summary for the test and fill at least all mandatory fields marked with an asterisk.

![](/Users/dfazlic/Documents/JIRA članak slike /Slika 9.png)

**Step 4**: When you are satisfied with the content of your test, click the Create button

> There you have it, your very own first test in Xray. For in-depth information about Xray and JIRA test integration you can [follow this link!](https://www.atlassian.com/devops/testing-tutorials/jira-xray-integration-manage-test-cases)





---

![Appbot review message in Slack](/img/dilbert-appbot-article.gif)

*Image downloaded from [dilbert.com](https://dilbert.com/strip/2022-02-01): 01-02-22 by Scott Adams*