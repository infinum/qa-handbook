## Version control

Regardless of whether you work as the only TAE on the project or with multiple people, there are some good practices you should follow when naming your git branches.

We can divide them into:

- permanent branches
- temporary branches


### Permanent branches

Permanent branches will most likely stay in your repository permanently.

**Main** (_master_)

- it should always be stable
- it should be up-to-date
- new code should only be merged after a code review
- should not be used for experimenting with the new code

**Development**

- used for checking the new code
- used for reviews
- gets merged into _main_ after passing a code review


### Temporary branches

Temporary branches, as the name indicates, are meant to live in the repository temporarily. Before starting work on a new feature or a test, you should check out a new branch. Once you are done with your work, and made sure everything works as expected, you can continue with merging the branch to develop/main after passing the code review.


### Branch naming

While permanent branches are mostly to be the same on all projects, you will have some more freedom with naming your temporary branches. Branch names should be short yet meaningful.

Often used names, or rather prefixes, are:

- Bugfix
- Hotfix
- Feature
- WIP

To further make clear what is being worked on in a specific branch, you can add a unique ID to the name, as well as a hyphen, underscore and slash. You can even add the author's name in the branch name to further distinguish who is working on which branch.

On whichever method you decide on, make sure to keep using it consistently.

Good branch names:

`wip-4827-add-login-test`

`username_wip_login_tests`

`fix/typos_in_test_data`


Bad branch names:

`bugfix`

`wip_add_test_that_checks_that_the_login_works`

`itisdifficulttoreadthenameofthisbranch`


### Pull requests (PR)

**Opening a PR:**

- Before diving into doing potential code-breaking changes in the repository, discuss them with your team.
  - E.g., configuration changes should be discussed beforehand.
- Keep PRs small and focused.
  - Focus on a single feature or test suite.
  - Keep configuration changes in a separate PR.
- Split commits into logical sections.
  - Avoid committing a bunch of unrelated files under a single ambiguous commit.
- Write short and meaningful commit messages.
- Add a description why the PR is necessary.


**Reviewing a PR:**

- Strive to review a PR within 24 hours.
- Carefully review the changes.
- Leave clear questions and comments in the appropriate lines of code/files.
- If you have a lot to discuss, consider jumping into a call instead of writing novels in the PR.

[How to handle pull requests without making enemies](https://infinum.com/blog/write-good-pull-requests/)
