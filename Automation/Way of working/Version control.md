## Version control

Regardless of whether you work as the only TAE on the project or with multiple people, there are some good practices you should follow when naming your git branches.

We can divide them into:

- permanent branches
- temporary branches


### Permanent branches

Permanent branches will most likely stay in your repository permanently.

**Main** (_master_)

- must always be stable
- should be up-to-date
- new code should only be merged after a code review
  - merge without PR should be disabled in repository settings
  - branch deletion should also be disabled, just in case :) 
- should not be used for experimenting with new code

**Development**

- can be used for checking new code
- should be used for reviews
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

To further make clear what is being worked on in a specific branch, you can add a unique ID to the name, as well as a hyphen, underscore, and slash. You can even add the author's name in the branch name to further distinguish who is working on which branch.

Whichever method you decide on, make sure to keep using it consistently.

Good branch names:

`wip-4827-add-login-test`

`username_wip_login_tests`

`fix/typos_in_test_data`


Bad branch names:

`bugfix`

`wip_add_test_that_checks_that_the_login_works`

`itisdifficulttoreadthenameofthisbranch`
