A key aspect to consider while testing is the concept of different deployment environments. These are usually self-contained spaces where an application lives and functions. Each environment is designed to serve a specific purpose in the lifecycle of a product, from its development to its release.

Different environments may be of different size and function. On one end, we have a big environment with large databases, connected to various external services and third party applications. On the other end, we have more contained, local environments that are not connected to outside services, but rather these external dependencies are simulated.

Simulating, or mocking, allows us to mimic the behavior of some external systems within a local environment. This is particularly useful when we want to test if some feature behaves as intended on our frontend, while an external environment is not yet connected or even developed on the backend – or when we want to test a specific edge-case that is not easily reproduced using actual systems.
Below we’ll run through some common deployment environments and what type of testing we usually perform on each.

## Development Environment (DEV) 

This is where an application is initially coded and built, it’s the devs playground, where they write, rewrite, test, and debug code. These environments are commonly deployed locally on the developer’s machine and we rarely have access to them, however in more complex environments there may be multiple development environments deployed externally, and everyone may have access to them.

We rarely have a reason to connect to the development environment, since the builds on these environments are usually a work in progress and not ready for QA testing.

## System Integration Testing Environment (SIT)

This is a testing phase where individual components of a product are combined and tested together to ensure that they interact correctly. When adding a new feature, this feature may involve adding a new (micro)service which needs to be tested to work in tandem with the rest of the system, so that it does not incorrectly modify or break other elements of the product or a larger system.

A SIT environment rarely have a large amount of data compared to other environments since the scope of testing is limited to integration. You may find yourself spending some time in this environment during the development of a fresh new feature, but not during smoke or regression testing.

## User Acceptance Testing Environment (UAT)

This is the final phase of testing, where QA, end-users, or clients check whether the software meets their needs and expectations. This environment is typically a mirror of the production environment, commonly with anonymized data to prevent privacy violations.

This is probably the environment where you’ll spend most of your time, doing sanity checks, smoke testing, regression testing, etc.

## Staging Environment (STA)

This environment is essentially a near-exact replica of the production environment, it includes the same hardware, software, databases, configurations, networking as the prod environment.
In some companies and on some projects, the staging environment may actually be connected to the production database, ensuring an internal “test in production” without actually deploying anything to the end-users. This is also known as a Pre-Production (Preprod) environment, ensuring we can perform final testing and ensure there are no unexpected surprises.

## Debug Environment

Some projects may have an environment dedicated to inspecting and fixing very specific issues, commonly used to test hard-to-reproduce issues found in production environments, usually reported by end-users.

## Other Testing Environments

As you may imagine there are plenty of other environment setups, here are some of the less common ones:

Functional testing environment: Here the software is tested for its functional requirements. Since some projects may have a preference for QA testing being done before moving on to the UAT phase.
Performance testing environment: This is a replica of the production environment used for conducting performance testing. It helps us understand how the application or a system behaves under different loads, how quickly it responds, its stability, and what are the limits.
Regression testing environment: This environment is used when performing regression testing, which involves rerunning all functional and non-functional tests to ensure that we didn’t introduce any breaking changes.
Security testing environment: In this environment, (penetration) testers check the software for potential security vulnerabilities.

On most of your projects you may use just one or two of these environments, commonly just SIT and UAT, however on some projects you may interact with many different environments. It is crucial to understand where each of these environments are positioned in a development cycle, however don’t take these definitions as set in stone. Each project has different loose definitions of what each of these environments' objectives may be, and how they’re used.

Whenever you’re joining a new project, it’s important to understand how their different environments are set up, which data you may expect each to have set up, and how you’ll be using them.

## Production Environment (PROD)

This is the main deployment environment we are all working towards, and this is the environment that the end-users interact with and use. While we have a fundamental rule to avoid testing in the production environment, there are some exceptions to the rule where we may perform a final smoke test of some new feature, or a crucial hotfix which cannot be otherwise confirmed.

You may assume that production tests on mobile platforms are run by simply downloading the app from the platform’s store. However, we leverage each platform’s beta testing before officially releasing the app to the general public.

### TestFlight and App Store Connect for iOS

Apple provides a framework through TestFlight and App Store Connect where we are able to release beta versions of our app to a select group of users. TestFlight is a separate app on your iPhone, through which you can download a beta version of the application.

In order to gain access to the TestFlight version of the application, ping a developer to add your account through App Store Connect.

### Google Play Beta for Android

Google offers a similar framework for beta testing. In order to gain access to beta versions of the app, a developer still needs to add your account as an internal tester. Once you’ve accepted the invite, you’ll need to join the beta through the app's Play Store page, and then you’ll have access to the beta app.

Although these services are primarily aimed to be used as beta testing, where we would obtain a pool of willing users to do beta testing and provide feedback, sometimes we use them to allow us to test the unreleased version of an application within production context.  This allows us to confirm that a feature works as intended, or a hotfix fixes a crucial issue.