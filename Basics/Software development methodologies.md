> *If everyone is moving forward together, then success takes care of itself.*

## Agile software development methodologies

The term **agile software development** refers to software development methodologies centered around the idea of iterative development. Requirements and solutions evolve through collaboration between self-organizing cross-functional teams. It enables teams to deliver products faster, with greater quality and predictability and greater aptitude to respond to change.


### What is it all about
- individuals and interactions over processes and tools
- working software over comprehensive documentation
- customer collaboration over contract negotiation
- responding to change over following a plan

There are many different agile project management methodologies used to implement the agile philosophy. Some of the most popular are Kanban, Lean, Dynamic System Development Model (DSDM) and Scrum. The latter will be in the focus of the following part as Scrum is primarly applied in our projects.

## Scrum
Scrum is an agile framework for developing, delivering and sustaining complex (software) products. It is designed for teams of ten or fewer members who break their work into goals that can be completed within time-boxed iterations (called sprints). The Scrum team tracks progress in 15-minute time-boxed daily meetings (called daily scrums). At the end of each sprint, a sprint review meeting is held to demonstrate the work which has been done, along with a sprint retrospective meeting to continuously improve the processes and practices.


## Scrum roles

### Stakeholders
Stakeholders are the purpose for which a product or service is created in the first place. They have certain requirements that need to be fulfilled. It is the responsibility of the Scrum team to fulfill the given requirements of the stakeholders and satisfy them. An important point that needs to be noted is that stakeholders are not always Product owners, but Product owners are always stakeholders.

### Scrum master
The Scrum master ensures the team lives agile values and principles and follows the processes and practices that the team agreed they would use.

The responsibilities of a Scrum master include:

- clearing obstacles
- establishing an environment where the team can be effective
- addressing team dynamics
- ensuring a good relationship between the team and Product owner as well as others outside the team (e.g. stakeholders)
- protecting the team from outside interruptions and distractions

### Product owner
- responsible for deciding which features and functionality to build and the
order in which to build them
- responsible for the overall success of the solution being developed
- actively collaborates with the Scrum Master and the development team
- represents the stakeholder (client) - the product is his main priority
- works on refining and prioritizing the product backlog

### Development team
- consists of people that "do the work": developers, designers, QA, operations
engineers
- preferably up to 9 people
- self-organizing and cross-functional
- executing the sprint (they get tasks from the product backlog and make decisions on how to get the work done)

![scrum-team.png](/img/scrum-team.png)


## Scrum ceremonies

### Sprint planning
The **sprint planning** is performed by the product owner, development team and Scrum master. 

The goal is to:

- determine the most important items of the product backlog to build in the next sprint
- break down each targeted feature into a set of tasks
- set a sprint goal - what the upcoming sprint is supposed to achieve


### Backlog refinement
The **backlog refinement**, also referred to as *product backlog grooming*, is the activity of creating and refining product backlog items, estimating and prioritizing them. It is a method for keeping the backlog updated, clean and orderly. The refinement meeting is (mostly) attended by the Scrum master, Scrum team and Product owner.


### Sprint review
The **sprint review** is a meeting held (mostly) on the last day of the sprint in which the team presents the results of the sprint to the stakeholders.

- attended by the development team, Scrum master, Product owner and the stakeholders
- the purpose is for the team to show the stakeholders the work they have accomplished over the sprint and compare it to the commitment given at the beginning of the sprint
- ideally, the results are discussed in a bidirectional information flow (aka *a conversation*)


### Sprint retrospective
The **sprint retrospective** is a team meeting held after the sprint review. It is an "improvement" meeting attended by all – the product owner, Scrum master, development team members, and only optionally with the stakeholders. 

Its goal is to:

- find ways to identify potential mistakes and seek out new ways to avoid those
mistakes
- identify good and the bad of the past sprint *(inspect-and-adapt)* - e.g. what activities and “things” the team is doing well, what activities should be continued and what can be done to improve the next sprint to be more enjoyable or productive


### Daily Scrum
The Daily Scrum, also referred to as the daily stand-up, is a (daily) recurring time-boxed meeting (e.g. 15 minutes or less) at which team members are taking turns answering three questions:

1. What did I accomplish since the last daily Scrum?
2. What do I plan to work on by the next daily Scrum?
3. What are the obstacles or impediments that are preventing me from making progress?

The goal is for everyone to understand the big picture of what is occurring.

![scrum-ceremonies.jpg](/img/scrum-ceremonies.jpg)

## Scrum artifacts

### Product backlog
The product owner is responsible for managing a prioritized list known as the **product backlog**. The product backlog might contain new features, changes to existing features, defects, technical improvements, etc. The product owner collaborates with internal and external stakeholders to gather and define the product backlog items.


### Sprint backlog
The collection of the tasks defined on the sprint planning meeting, along with their associated product backlog items, forms a second backlog called the **sprint backlog**.


### User stories
- usually written by the Product owner
- user stories (features) are made up of tasks
- every story and task are estimated with points
- describe a desired feature's functional requirement - usually in narrative form (many formats)
- contain acceptance criteria that a user story needs to fulfill to be accepted
- ideally, they should follow the INVEST rule: **I**ndependent, **N**egotiable,
**V**aluable, **E**stimable, **S**mall, **T**estable

**Acceptance criteria** can be formally or informally written. 

An example of a formal method is the "given-when-then" (GWT) format: 

- **Given** some context
- **When** some action is carried out 
- **Then** a particular set of observable consequences should obtain

Real-world example:

- **Given** my bank account contains sufficient funds,
- **When** I attempt to withdraw an amount less than my card's limit,
- **Then** the withdrawal should complete without errors or warnings

Some other best practices:

- Write them from the end-user's perspective
- Break them down into concise chunks so they are easier to understand
- Make sure that each criterion is precise and testable
- Make sure to include both functional and non-functional criteria when applicable

If your project doesn't come with any acceptance criteria, try to change that by discussing it with the team. Writing good documentation helps transparency and getting things right on the first attempt.

### Product increment
The Product increment is the sum of:

- all Product backlog items completed during a sprint
- the value of the increments of all previous sprints

At the end of a sprint, the new increment must be "done", which means it must be in a useable condition and meet the previously set *Definition of Done*.

## How a Scrum sprint looks like
In Scrum, work is performed in iterations or cycles of usually **two** to
**four** weeks. The work completed in each sprint should create something of tangible value to the customer or user.

Sprints:

- are time-boxed
- have a fixed start and end date
- should all be of the same duration

Sprint process:

1. the Product owner creates the product backlog
2. Sprint planning is done at the beginning of the sprint (there it is decided what the sprint goal is and stories/tasks from backlog are taken into the Sprint backlog)
3. during the sprint user stories are being worked on from Sprint backlog
4. at the end of a sprint the team should have a "potentially shippable product"
5. the sprint ends with sprint demo and sprint retrospective meetings

![scrum-sprint.jpg](/img/scrum-sprint.jpg)

## Definition of Ready & Done

### Definition of Ready

**Definition of Ready** means that user stories must be immediately actionable. The team must be able to determine what needs to be done and the amount of work required.

When should a task be moved from the backlog to the shortlist? There is no one-size-fits-all solution here, but a good rule of thumb is:

- It should contain some acceptance criteria which tell the developer what needs to be done and tell you how a certain feature should behave in order to be deemed acceptable.
- It should contain links to the design specification (e.g. Figma links) if the task is about implementing new UI.
- It should contain links to other specification documents, e.g. database models or API.

A task missing some of the components mentioned above will be difficult or impossible to test properly. You should act upon this to get it specified.

### Definition of Done

**Definition of Done** drives the quality of work and is used to assess when a user story has been completed.

When is a task done from the perspective of a software tester?

- A simple way of looking at it: when all of the acceptance criteria are met.
- A more complex way of looking at it: when all of the acceptance criteria are met, you have defined all of the test cases, and when there are no outstanding functional or non-functional issues pertaining to that task.
- Sometimes there will be no acceptance criteria and the definition of done will be your gut feeling.

All of the above will vary from project to project and tester to tester.


## Estimations

Estimations can be done in different ways. The two most common principles used for estimating are:

- **time estimates** - estimations are given using specific time frames (e.g. hours, days, weeks, months)
- **story points** - rate the relative effort of work in a Fibonacci-like format (0, 0.5, 1, 2, 3, 5, 8, 13, 20, 40, 100). They are used to estimate the overall effort required to fully implement a product backlog item and are assigned relative to work complexity, the amount of work and risk or uncertainty.

Traditional software teams usually give estimates in a time format, while agile teams tend to use story points instead. 


### Story points and planning poker
Teams starting with story points use an exercise called **planning poker**. During planning poker, the team takes an item from the product backlog, discusses it briefly and each team member formulates an estimate. Then everyone holds up a card with the number that reflects their estimate. If everyone agrees, great! If not, they take some time to understand the rationale behind different estimates.

*The information was taken from [Atlassian's blog pages](https://www.atlassian.com/agile/project-management/estimation) where you can read more about estimations and agile project management.*

## Burndown & velocity charts

### Burndown chart
A **burndown chart** is a graphic representation of how quickly the team is working through user stories. It shows the total effort against the amount of work.


### Velocity chart
The **velocity chart** is a graphic representation of the amount of value delivered in each sprint, enabling you to predict the amount of work the team can get done in future sprints. It is useful during your sprint planning meetings to help you decide how much work you can feasibly commit to.


## Scrum vs Kanban 
Scrum and Kanban are both iterative work systems that rely on process flows. However, there are a few main differences between the two:

![scrum-vs-kanban.png](/img/scrum-vs-kanban.png)
