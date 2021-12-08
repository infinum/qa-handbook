> *I have not failed. I've just found 10.000 ways that won't work.*

## Tasks? Backlog?

When you look at a project from the perspective of a project management tool, a project is nothing but a collection of tasks.
How these tasks move about is crucial to your work.

Generally, each project has a backlog. A backlog is a collection of everything that should be done. The backlog should always be prioritized, i.e. ranked from most to least important.

## Task management on Productive

Once a task is pulled from the Backlog into the Shortlist, it means it is next in line to be worked on:

**Backlog -> Shortlist**

Once the dev actually starts coding it, he/she will transfer the task into the Current list:

**Shortlist -> Current**

A task ends up in the QA task list once the implementation has been completed and the developer has tested the feature without finding any obvious issues:

**Current -> QA**

If the task is in the QA list but still assigned to the developer, it means he/she is yet to deploy a new build or push the changes to a test environment. Once the task is assigned to you, it is time for testing.

If no bugs are found QA closes the task (if the client is not doing testing).

**QA -> UAT** (if the client is doing testing)

If any bugs are found, the path is reversed:

**QA -> Shortlist**

If the task had only minor issues associated with it, you can close it and open new bugs in the Backlog.

The developer will assign the task back to QA once he establishes that an issue has been fixed:

**Shortlist -> Current -> QA**

This back-and-forth process may take multiple iterations until the QA team closes it or deems the feature ready for user acceptance testing (UAT), which is usually done by the client. If client-side testing results in any additional issues, the process starts all over again:

**UAT -> Shortlist -> Current -> QA -> UAT**

You should strive to have as few as possible tasks returned from UAT. This means you have missed something. It's expected and normal that there will be issues you did not manage to catch, but you should do whatever you can to keep it at a minimum.

If you find a lot of issues that originated in a task, it is perfectly fine to open separate tasks just for that issue and reference them in the original one. Once they are all done and checked, you can move the original task onwards.

In general, there are two types of tasks you will deal with:

- **Feature tasks:** used to implement new features.
- **Bug tasks:** used to fix issues found in the implementation.

Each task should only be opened for one person and one platform. E.g., if both Android and iOS are implementing the same feature, they should have separate tasks.

### Closing QA tasks

If the client is not doing testing, and no bugs were found while testing a feature task or the task had only minor issues associated with it, you can close it and open new tasks in the Backlog. The same applies to bugfix tasks. 

When closing a QA task, you should always add the following information:

- all devices/browsers on which you tested it
- build/platform/environment that you used while testing
- how and what you tested (you don't need to go into every single detail; a brief description with the most important information will be fine)
- any other information that might be of importance (e.g. what issues you found).

This way, if you or someone else ever needs to go back to that task, you will have the information about what was done and what the status of the feature/bugfix was when closing the task.


## Bug tasks - severity and priority

Not all bugs are the same. You can attribute severity and priority to a bug in order to communicate to the team how important it really is and triage it appropriately.

**Severity** is related to how damaging it is to the product.

**Priority** is related to how soon should a fix mitigating it be deployed to production.

Sometimes a bug can have low severity, but high priority. E.g. imagine uploading a wrong logo on the website.

Here's one possible way of classifying them according to severity and priority:

**Severity:**

- Safety: Safety issue. The product creates a dangerous situation.
- Blocker: Prevents function from being used, no work-around, and blocking progress in multiple screens or components.
- Critical: Prevents a function from being used, no work-around being available.
- Major: Prevents a function from being used, but a work-around is possible.
- Normal: A problem making a function difficult to use and no special work-around is required.
- Cosmetic: Small issue that does not significanly impact the product.

**Priority:**

- High: It should be fixed immediately.
- Normal: It should be fixed in the next development iteration (sprint) or in the next version.
- Low: It should be fixed at a later point.


---

![task-management.gif](/img/task-management.gif)
