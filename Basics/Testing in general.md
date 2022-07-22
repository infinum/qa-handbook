> *You can be a great tester if you have programming skills. You can also be a great tester if you have no programming skills at all. And, you can be a lousy tester with or without programming skills. A great tester will learn what skills she needs to continue to be great, in her own style.*

## Testing is...

...difficult. :-)

- There is no way to ensure all bugs have been found or fixed.
- It is hard to determine which bugs are important and which are not.
- It is impossible to be completely sure something works.
- You cannot test on all possible combinations of software and hardware.
- There are multiple ways in which something can fail.
- Even if something doesn't fail, the app can still be bad.

Keeping that in mind, you should do the best possible job to drive what the team is working on forwards to the best possible quality, keeping in mind the context of the product and the project.

This document is a short primer and introduction into all things called software testing. There is no particular order.

You can also use the [Wiki article for software testing](https://en.wikipedia.org/wiki/Software_testing) or the [ISTQB syllabus](https://www.istqb.org/certifications/certified-tester-foundation-level) as a starting point.

## Testing a feature

This is just a very rough approach for testing a certain feature. What you do in between is what actually counts for which the rest of this Handboook should provide plenty of inspiration.

1. Examine all the specs and see if anything is missing
2. Write test cases according to acceptance criteria
3. Explore the feature freely
4. Try the happy flows according to specs
5. Try the unhappy flows and edge cases
6. Check the design and interactions on several devices and/or browsers
7. Do a smoke test of the rest of the app to quickly find out if anything else was broken
8. Report any fresh issues

## 7 Basic Principles of the Context-Driven School

A balanced approach to software testing, taking into the consideration all aspects of a given project, will usually mean taking varied approaches depending on what the project calls for.

This means there is no silver bullet in software testing, but you can always take a hint from the context-driven school:

- **The value of any practice depends on its context.**

- **There are good practices in context, but there are no best practices.**

- **People, working together, are the most important part of any project’s context.**

- **Projects unfold over time in ways that are often not predictable.**

- **The product is a solution. If the problem isn’t solved, the product doesn’t work.**

- **Good software testing is a challenging intellectual process.**

- **Only through judgment and skill, exercised cooperatively throughout the entire project, are we able to do the right things at the right times to effectively test our products.**

## 7 principles of software testing

Here's a more old-school list of software testing principles:

- **Testing shows the presence of defects, not their absence**

Testing can show that defects are present, but cannot prove that there are no defects. Testing reduces the probability of undiscovered defects remaining in the software but, even if no defects are found, testing is not a proof of correctness.

- **Exhaustive testing is impossible**

Testing everything (all combinations of inputs and preconditions) is not feasible except for trivial cases. Rather than attempting to test exhaustively, risk analysis, test techniques, and priorities should be used to focus test efforts.

- **Early testing saves time and money**

To find defects early, both static and dynamic test activities should be started as early as possible in the software development lifecycle. Early testing is sometimes referred to as shift left. Testing early in the software development lifecycle helps reduce or eliminate costly changes.

- **Defects cluster together**

A small number of modules usually contains most of the defects discovered during pre-release testing, or is responsible for most of the operational failures. Predicted defect clusters, and the actual observed defect clusters in test or operation, are an important input into a risk analysis used to focus the test effort.

- **Beware of the pesticide paradox**

If the same tests are repeated over and over again, eventually these tests no longer find any new defects. To detect new defects, existing tests and test data may need changing, and new tests may need to be written. (Tests are no longer effective at finding defects, just as pesticides are no longer effective at killing insects after a while.) In some cases, such as automated regression testing, the pesticide paradox has a beneficial outcome, which is the relatively low number of regression defects.

- **Testing is context dependent**

Testing is done differently in different contexts. For example, safety-critical industrial control software is tested differently from an e-commerce mobile app. As another example, testing in an Agile project is done differently than testing in a sequential lifecycle project.

- **Absence-of-errors is a fallacy**

Some organizations expect that testers can run all possible tests and find all possible defects, but principles 2 and 1, respectively, tell us that this is impossible. Further, it is a fallacy (i.e., a mistaken belief) to expect that just finding and fixing a large number of defects will ensure the success of a system. For example, thoroughly testing all specified requirements and fixing all defects found could still produce a system that is difficult to use, that does not fulfill the users’ needs and expectations, or that is inferior compared to other competing systems.

## Rapid Software Testing

Rapid Software Testing is a methodology and a class about it, authored by James Bach and Michael Bolton, focused on doing the fastest, least expensive testing that still completely fulfills the mission of testing.

## Types of testing

It is hard to enumerate all ways in which you can test software.

What is a test anyway? One way to look at it is that a test is anything you do with software that will give you insight into how it behaves under certain conditions. But we could debate that until we're in a drunken stupor. Have a look at [Michael Bolton's opinion on the topic](http://www.developsense.com/blog/2014/10/testing-is/) as well.

Let's be a bit more pragmatic and look at one possible categorization of the types of test you can conduct. 

N.b., this categorization does not cover every single test type you can execute.

### According to approach:

![continuum.jpg](/img/continuum.jpg)

The way you test ranges from fully formal/algorithmic/scripted to fully random.

**Script-based testing** is slow and tedious, but good for confirming previously implemented functionalities are still working as expected.

**Exploratory testing** is faster at finding critical issues, usability problems, and unforeseen circumstances, but is usually incomplete and not fully reliable since it heavily depends on the tester's skill and experience.


### According to focus:

You have to determine what will you focus on when you do testing. It is good to focus on one thing to keep your mental capacities sharp.

We can crudely divide the focus into two categories: **functional** and **non-functional** testing.

**Functional testing**

The goal of functional testing is to verify that the application is behaving the way it was envisioned to.

When doing functional testing, you should both rely on the requirements set out in a particular task, and think outside the box to find ways in which these requirements might be wrong or insufficient.

**Non-functional testing:**

Non-functional testing is used for testing those areas of a certain software product that is less concerned with "what it does" which doesn't make it any less important.

- UI testing
- Localization testing
- Usability testing
- Accessibility testing
- Performance/Load/Stress testing
- Security testing
- etc.

### According to scope:

Sometimes you don't want to test the entire app.

- Smoke/sanity/build verification testing
- Confirmation testing
- Regression testing

We use smoke testing to verify that a certain build of the product is stable enough to be further tested and that all major, obvious features are not heavily broken.

Confirmation testing is done to check that a certain bugfix resolved a previous issue.

Regression testing is used at certain milestone points in the app lifecycle (e.g. before the release) to catch some specific failing cases that might not have been tested often during development.


## What is exploratory testing?

![exp-vs-for.png](/img/exp-vs-for.png)

**Exploratory testing** is probably the fastest and most efficient way of finding issues in software products, but it's not the only way nor just doing whatever you want.

Exploratory testing is to traditional testing what agile is to waterfall, it cuts the time taken to prepare yourself for testing to almost zero since in exploratory testing you **simultaneously design and execute the tests**.

When doing exploratory testing you should:

- Determine a time you will spend, e.g. 2 hours
- Determine how many sessions you will have
- Determine whether you will test alone or with someone else
- Determine a goal of your testing
- Determine an approach you will take
- Write down all the questions you had
- Write down the steps you have taken
- Write down the issues you have found

Sometimes, all of the above is planned via an **exploratory testing charter**. Other people really like using mind maps. In any case, the whole point is in investigating and freely exploring what you have set out to test. You will need to find out which test planning method works best for you.

Read more on exploratory testing from [Cem Kaner](https://secureservercdn.net/198.71.189.51/13j.276.myftpupload.com/pdfs/QAIExploring.pdf) or [James Bach](https://www.satisfice.com/exploratory-testing).

## Types of testing - A fuller list

[This list](https://www.softwaretestinghelp.com/types-of-software-testing/) is by no means exhaustive, but it might just get you to dig deeper into certain areas that might help your software project.

## How do other companies do testing?

See the [howtheytest](https://github.com/abhivaikar/howtheytest/blob/master/README.md) GitHub repo.
