> *The most exciting phrase to hear in science, the one that heralds discoveries, is not ‘Eureka!’ but ‘Now that’s funny'...*


## Checklist

- Make sure all features are merged in the release candidate build and that the respective backend features are deployed to your test environment.
- Run a regression test of the release candidate on a non-production environment by following the test suite.
- Make sure to check the Prince of Versions scenarios for mandatory and optional updates.
- If any bugs are found, discuss it with the team, have them create another release candidate if the bug is a blocker.
- Retest the affected area of the app in each test candidate.
- Create a test report and share it with the team.
- Submit the app to its respective store.
- Install the current store build from the store.
- Set it up and update it with the new Google Play Beta/Testflight build.
- Do a limited regression test on production to check the most important flows and functionalities.
- Publish the app to a limited part of the audience (phased/staged release).
- Check Crashlytics daily until the percentage is up to 100%.
- Stop the phased/staged release in case of crash spikes, create a hotfix build and repeat the process.

Other than the Google Play / App Store specifics, most of the above is also valid for regression testing web or desktop apps.


## Regression testing best practices

There is no silver bullet when it comes to regression testing, but here are some best practices we gathered throughout the years.

- Make sure to discuss the scope and effort needed with your team. Keep informing the team of your progress.
- Report bugs as soon as possible after uncovering them.
- Organizing a testing session with multiple people will give you confidence and uncover issues fast.
- Mix it up - don't use the same devices and browsers from regression test to regression test. In that way you'll be covering more of the spectrum each time you do it.
- Have your test cases ready before going into regression testing.
- Don't go too deep into all the features, optimize the test in a way to touch all areas of the app but also focus on those features that are truly critical and/or have been affected by the new release.
- Make exploratory testing part of your regression test. The test cases themselves are a great guide, but you should rely on your instinct as well.
- Make sure your test environment is as close as possible to production.
- If you have automated parts of the app, focus on manually testing those parts that were left unchecked, but don't completely ignore those that were covered.


---

![dilbert-user.gif](/img/dilbert-user.gif)
