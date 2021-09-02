> *Those who plan do better than those who do not plan even though they rarely stick to their plan.*

## What is a software project?

All software projects at Infinum are different, but all software projects at Infinum are also pretty much the same.

Each software project in active development will usually have one or more members from these respective teams:

- **Development team** (backend, frontend, iOS, Android, Flutter, Wordpress...)
- **Design team**
- **Project management team**
- **Growth team**
- **QA team**

These people make up a project team. The role of the project team is to:

- Squeeze every last drop of information from the client.
- Create design materials for the application.
- Code and test the application.
- Deploy the application to production.
- Maintain the application and adjust it according to client/market demands.
- Take care of the customers.

So there are three sides to a software project at Infinum:

- **Infinum's project team**
- **The client**
- **The application**

And each project has the following constraints:

- **Time**
- **Budget**
- **Quality**

While deadlines and money are things that definitely affect the scope of a project, your job is to **always focus on quality above all else**.

This is why companies have quality assurance, because when there is a _separation of concerns_, there's also space for someone who puts overall quality first. Developers primarily care about code quality, designers primarily care about UI and UX, and you can primarily care about how these two get together to form a perfect little application that will please the client, please the audience, and be the envy of many.

**While other people's motivation might change, yours never does.** In full recognition that quality is a team effort and everyone should drive towards it, you must always stay aware that it is your first and foremost responsibility.

Of course, you as a project member are also responsible to take care of time and budget in the ways that pertain to your line of work:

- By **staying wary of scope creep**. If a client reports a bug which does not conform to the original specification, discuss with the entire team whether it should be treated as a defect (a mistake made on our part) or as a change request (a _mistake_ in the agreed upon specification). Scope creep is costly and bites people on the ass.
- By **deprioritizing silly bugs**. Sometimes we need minimum viable products out fast. These products are meant to tickle the market's fancy and allow the client to adjust his idea according to feedback. In such an environment, performance on obscure devices is not crucial, killer features working well are crucial.
- By **finding issues fast**. Exploratory and smoke testing are your best friends when all you need to do is find some critical issues in a matter of minutes.
- By **deploying quality**. Nothing is most costly than a bad build going to production. Never let that happen.
- By **writing good bug reports**. More on this later, but the main principle here is to be concise and consistent at all times.
- By **communicating all the time** and thus helping speed things along. Share info between the team and the client; share info between team members. You know the app best and have valuable information that is worth spreading to everyone.

This is how all software projects are the same. The only way to convey how they differ among each other is for you to go out there and start facing specs, bugs, clients, deadlines...

## Project phase lifecycle tl;dr

This will all be elaborated below, but here's a short **tl;dr** on what a project's phase will look for you from beginning to end. For the purposes of this example, the focus is on mobile apps.

1. Help out with the definition of designs and requirements (make sure you are active during meetings)
2. Test feature tasks and report bugs and UI/UX improvements
3. Write test cases for each feature and automate certain aspects of testing
4. Continue testing until bugs are resolved and a final build is ready
5. Before release, do an update test and full regression test
6. Check that build in the production environment (Google Play Beta, Testflight)
7. Release the app (preferably using staged/phased releases)
8. Check our crash reporting tools for spikes (e.g. Crashlytics)

## A project's rhythm

A project has its motions and paces. For you as a QA engineer, it will predictably speed up and slow down several times in its lifetime.

This is how we can break down a typical software project in time.

### Bizdev phase
- **Description:** People doing business do some correspondence and sign some papers. Their job is very challenging, but it's not the focus of this Handbook.

- **Your obligations:** Basically none, you can have a cup of coffee.

### Research phase
- **Description:** The design team works on brand/domain research and create a reference for the app's look and feel.

- **Your obligations:** If you are versed in these matters, you can help out with interviews, brainstorming the flow, and giving input on the eventual look-and-feel. Sometimes we get involved, sometimes we won't.

### Design phase
- **Description:** The design team works on UI elements, screens, microinteractions, and UX in general.

- **Your obligations:** You can help out by commenting on their solutions in person, on refinement meetings, or via Invision / Zeplin. If any usability testing is being conducted, you can certainly help out devise tests and execute them. Read more on how to collaborate with designers in this [blog post by Nikolina](https://infinum.co/the-capsized-eight/the-qa-fairy-godmother-10-practices-for-happily-ever-after).

### Pre-development phase
- **Description:** On most projects, this is not a relevant phase for us, but we are mentioning it for the sake of completeness.

- **Your obligations:** Create a test strategy document which defines what will be tested, how it will be tested, who and when will test it, how testing will be documented, which criteria and KPIs will be used for assessing quality, etc. More on this later.

### Development phase
- **Description:** This is when the development team works on defining and coding the app.

- **Your obligations:** Your job is to help define features, continously test new features, write test cases, automate testing, and report issues. The bulk of your work lives here.

### Pre-release phase
- **Description:** When the entire team prepares to release new code into production.

- **Your obligations:** Doing a regression test by using test documentation, doing update tests, singling out critical bugs and green-lighting the release. Additionally, sanity checking the app on Testflight and Google Play Beta and letting it out into the wilderness. This is the *make-it-or-break-it* phase.

### Post-release phase
- **Description:** When the team monitors the app's performance in order to find any unforeseen issues.

- **Your obligations:** Use Fabric, Firebase Crashlytics, Appbot, and other tools at your disposal to catch any major issues and report them back to the team.

### Always
Whatever phase the project might be in, you can always:

- Help project managers with task management and definition
- Help organize the team (scrums, design reviews, testing sessions, ad hoc meetings to reach consensus on issues...)
- Help the client test and understand the app
- Help maintain the team spirit

## Main and support tester
Since we have a lot of projects and projects are not always in sync with each other, a tester's load might go up and down during the year.

To mitigate this and avoid overtime, most projects have a **main tester** and a **support tester**.

A main tester can redistribute his/her workload to the support tester when he/she is simply not able to meet the project's demands.

In case you're the **main tester** and you're not sure whether your project has a **support tester** assigned or not, you can check with your team and ask someone to take this responsibility.

## Onboarding someone new to a project

### What you can do:
* Set-up: invite the new person to all the relevant meetings, Slack channels, Firebase, Zeplin/Figma, Polyglot and all the others (VPN, JIRA, Teams etc.)
* Start by explaining the big picture - what type of project is this, how it all began, how long are we working on it
* Continue with more detailed specs:

1. Talk about work processes
2. Introduce the team - who are the people you are going to be working with, what do they do, what are they like, what type of communication is expected
3. Always make yourself available for questions and answer them the best way you can 
4. Share some tips and tricks
5. Overlook (in a helping manner) the work done and help remedy the mistakes

## Being onboarded to a new project

* Ask, ask, ask & - you guessed it - ask! If you feel uncomfortable, make a list of non-urgent questions and send them in bulk once a day
* It is perfectly normal and desired to have many questions at the beginning 
* Everyone, especially at Infinum, understands that you are new and it is ok that you don't know everything yet and might not have all the answers
* Keep an eye on Slack channels
* Create all necessary accounts as soon as you receive invitations to services in order to be ready when you need them
* Question *status quo* - fresh blood is good to have
* Try helping yourself with mental maps

## Software development methodologies

There are plenty of ways to organize a software project. Since your job is to take care of testing and other quality processes, it is important that you are familiar with different approaches.

More on this later, but for now, check out this cute graphic...

![project-methodologies.jpg](/img/project-methodologies.jpg)

---

![working-on-projects.gif](/img/working-on-projects.gif)
