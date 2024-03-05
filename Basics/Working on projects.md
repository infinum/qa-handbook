> *Those who plan do better than those who do not plan even though they rarely stick to their plan.*

## What is a software project?

All software projects at Infinum are different, but all software projects at Infinum are also pretty much the same.

Each software project in active development will usually have one or more members from these respective teams:

- **Development team** (backend, frontend, iOS, Android, Flutter, Wordpress...)
- **Design team**
- **Project management team**
- **Product Data Analytics**
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

A project has its ebbs and flows. As a QA engineer, you can expect it to fluctuate in speed and intensity at various stages throughout its lifecycle. Let's dive into the breakdown of a typical software project timeline:

### Bizdev phase

- **Description:** During this phase, business-related activities, correspondence, and paperwork take precedence. While essential, this phase is not the primary focus of this Handbook.

- **Your obligations:** Your involvement in this phase is minimal, giving you time to enjoy a cup of coffee.

### Research phase

- **Description:** The design team engages in brand and domain research, creating a reference for the app's aesthetics and user experience.

- **Your obligations:** If you have expertise in these areas, your assistance may be sought for interviews, brainstorming sessions, and input on the app's eventual look and feel. Your level of involvement may vary depending on the project.

### Design phase

- **Description:** The design team concentrates on UI elements, screens, microinteractions, and overall user experience.

- **Your obligations:** You can contribute by offering feedback on their solutions during in-person discussions, refinement meetings, or through tools like Invision or Zeplin. If usability testing is conducted, you can assist in devising and executing tests. For more insights on collaborating with designers, refer to [Nikolina's blog post](https://infinum.co/the-capsized-eight/the-qa-fairy-godmother-10-practices-for-happily-ever-after).

### Pre-development phase

- **Description:** While not applicable to most projects, this phase is mentioned for completeness.

- **Your obligations:** Your role is to create a comprehensive test strategy document outlining what will be tested, how, by whom, when, and how testing will be documented. It should also specify the criteria and KPIs for assessing quality.

### Development phase

- **Description:** This is when the development team defines and codes the app.

- **Your obligations:** Your primary responsibilities include feature definition, continuous testing of new features, test case creation, test automation, and issue reporting. The majority of your work occurs during this phase.

### Pre-release phase

- **Description:** This phase involves the entire team preparing to release new code into production.

- **Your obligations:** You will conduct regression testing using test documentation, perform update tests, identify critical bugs, and give the green light for release. Additionally, you will sanity check the app on platforms like Testflight and Google Play Beta before releasing it to the public. This phase can make or break the project's success.

### Post-release phase

- **Description:** In this phase, the team monitors the app's performance to detect any unforeseen issues.

- **Your obligations:** Utilize tools such as Fabric, Firebase Crashlytics, Appbot, and others at your disposal to identify and report major issues back to the team.

### Always

Irrespective of the project phase, you can always:

- Assist project managers with task management and definition.
- Play a role in organizing the team through activities like scrum meetings, design reviews, testing sessions, and ad hoc meetings to reach consensus on issues.
- Help the client understand and test the app.
- Contribute to maintaining a positive team spirit.

## Onboarding someone new to a project

**What you can do:**

* Set-up: invite the new person to all the relevant meetings, Slack channels, Firebase, Zeplin/Figma, Polyglot and all the others (VPN, JIRA, Teams etc.)
* Start by explaining the big picture - what type of project is this, how it all began, how long are we working on it
* Continue with more detailed specs:

1. Talk about work processes
2. Introduce the team - who are the people you are going to be working with, what do they do, what are they like, what type of communication is expected
3. Always make yourself available for questions and answer them the best way you can 
4. Share some tips and tricks
5. Overlook (in a helping manner) the work done and help remedy the mistakes

## Software development methodologies

There are plenty of ways to organize a software project. Since your job is to take care of testing and other quality processes, it is important that you are familiar with different approaches.

More on this later, but for now, check out this cute graphic...

![project-methodologies.jpg](/img/project-methodologies.jpg)
