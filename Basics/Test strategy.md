> *Walking on water and developing software from a specification are easy if both are frozen.*

A test strategy is a document that serves as a basis detailing how quality processes are implemented on a certain project.

Since the domains, budgets, and architectures can vary a lot between projects, there is no single test strategy that would cover all grounds. This article briefly explains what such a document should elaborate on. 

Use these guidelines if you are ever tasked to assemble a test strategy or when thinking about how to approach your next project.

## Automation

- What amount of coverage do we want to achieve?
- When will we run automated tests?
- Which tests should we run and maintain? Unit tests, API tests, UI tests, load tests, security tests?
- Do we need a separate environment for running tests?

## Definition of ready

When should a task be moved from the backlog to the shortlist?

There is no one-size-fits-all solution here, but a good rule of thumb is:

- It should contain some acceptance criteria which tell the developer what needs to be done and tell you how a certain feature should behave in order to be deemed acceptable.

- It should contain links to the design specification (e.g. Zeplin links) if the task is about implementing new UI.

- It should contain links to other specification documents, e.g. database models or API.

A task missing some of the components mentioned above will be difficult or impossible to test properly. You should act upon this to get it specified.

## Definition of done

When is a task done from the perspective of a software tester?

A simple way of looking at it: when all of the acceptance criteria are met.

A more complex way of looking at it: when all of the acceptance criteria are met, you have defined all of the test cases, and when there are no outstanding functional or non-functional issues pertaining to that task.

Sometimes there will be no acceptance criteria and the definition of done will be your gut feeling.

All of the above will vary from project to project and tester to tester.

## Entry and exit criteria

- When can we start testing a certain feature?
- When is a feature done?

## Environments

- Which environments will be used for testing and when?
- Oftentimes day-to-day activities are carried out on the "development environment" while prerelease testing is executed on a more stable (production-like) enviornment.
- Will we have to run some tests in production?

## Functional and non-functional requirements

- How are the functional and non-funcational requirements written down?
- How will we check that non-functional requirements are satisfied?

Test cases are usually derived from acceptance criteria and expanded by using heuristics and experience. 

If acceptance criteria are found in a user story or a task, they should be mapped to test cases in order to ensure traceability.

Here's a quick intro to acceptance criteria.

### Acceptance criteria
Each work item that will be coded and integrated into the final product should have acceptance criteria. The implementation should satisy user-level criteria in order to be successful.

Acceptance criteria can be formally or informally written. 

An example of a formal method is the "given-when-then" (GWT) format: 

- _Given some precondition_

- _When I do some action_

- _Then I expect some result._

Some other best practices:

- Write them from the end-user's perspective
- Break them down into concise chunks so they are easier to understand
- Make sure that each criterion is precise and testable
- Make sure to include both functional and non-functional criteria when applicable

If your project doesn't come with any acceptance criteria, try to change that by discussing it with the team. Writing good documentation helps transparency and getting things right on the first attempt.


## Severity and priority

Not all bugs are the same. You can attribute severity and priority to a bug in order to communicate to the team how important it really is and triage it appropriately.

**Severity** is related to how damaging it is to the product.

**Priority** is related to how soon should a fix mitigating it be deployed to production.

Sometimes a bug can have low severity, but high priority. E.g. imagine uploading a wrong logo on the website.

Here's one possible way of classifying them according to severity and priority:

**Severity:**

- Safety. Safety issue. The product creates a dangerous situation.
- Blocker: Prevents function from being used, no work-around, and blocking progress in multiple screens or components.
- Critical: Prevents a function from being used, no work-around being available.
- Major: Prevents a function from being used, but a work-around is possible.
- Normal: A problem making a function difficult to use and no special work-around is required.
- Cosmetic: Small issue that does not significanly impact the product.

**Priority:**

- High: It should be fixed immediately.
- Normal: It should be fixed in the next development iteration (sprint) or in the next version.
- Low: It should be fixed at a later point.

## Test cases

- Will we write and maintain test cases?
- Which tool will we use?

## Test deliverables

- What is the output of our testing? 
- Is it just bugs or will we provide a detailed test report?

## Test environment

- Which devices will be used for testing?
- Which OS versions will be used for testing?
- Which browsers should we support?

## Test plans

- Which types of tests will we run and when?
- Will regression tests include all test cases or just a subset?
- Who will assemble and carry out test plans during development?
- Will we run testing sessions with the entire team?
- What will these plans include?

---

![test-strategy.gif](/img/test-strategy.gif)
