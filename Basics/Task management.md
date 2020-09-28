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


---

![task-management.gif](/img/task-management.gif)
