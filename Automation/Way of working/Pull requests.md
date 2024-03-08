## Pull requests (PR)

Guidelines on how to work with pull requests (PR).

## Preconditions

Before creating a pull request, make sure:

* Your code is working as expected 
  * You have tested both positive and negative scenarios
* There is no dead code or unnecessary comments
    * If there are docstrings / comments, they must be up-to-date
* You have followed the style guide and linted the code
* You have merged the base branch into the current working branch
* Your commits are small and focused, split into logical sections
    * Commit messages should be clear, concise and meaningful
    * Avoid committing a bunch of unrelated changes under a single commit

## Opening a PR

When creating a PR, make sure:

* The PR is small and focused
    * Focus on a single feature or test suite
    * Keep configuration changes in a separate PR
* The PR title is clear and concise
* The PR has a short summary of changes and reasoning behind them
    * Relevant links to tasks should also be included
* You have done a self-review
    * Always check your code before asking for a review
    * The code must work on your machine without any issues 
* You have merged the base branch into the current working branch
    * It ensures that you are working with the latest changes
    * It reduces the chance of a conflict
* You added the appropriate reviewers
    * To simplify, add default reviewers for pull requests in the project settings
* You selected the correct target branch
* You updated the appropriate documentation
    * Project README, tasks, Confluence, etc.

## Feedback / PR review

* Strive to review a PR within 24 hours
* Carefully review the changes
    * In case of more complex changes, run the code locally to make sure everything works as expected
* Leave clear questions and comments in the appropriate files / lines of code
    * If you have a lot to discuss, consider jumping into a call before leaving a bunch of comments

## Implementing feedback

* Focus on updating the code discussed in the comments
* Do not add additional code that was not discussed or is not needed at the moment
    * Leave that for another PR

## When and who merges a PR?

You, the developer that opened the PR, are responsible for merging it to the target branch.

You can merge the pull request when: 

* The agreed number of reviewers have checked and approved it
* All comments and tasks have been resolved
    * The developer that opened a comment or a task is the one that closes it after the updates have been implemented and checked


### Additional resources

* [Creating a pull request](https://infinum.com/handbook/frontend/code-quality/creating-a-pull-request)
* [How to handle pull requests without making enemies](https://infinum.com/blog/write-good-pull-requests/)
