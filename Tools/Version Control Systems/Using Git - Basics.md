> *Fellow testers, we cannot not to find bugs.*

## What is git?
Git is a **Version Control System** (VCS). There are various version control systems, but `git` is by far the most popular one, both for individual and company use. On a very basic level, there are a couple of awesome things a VCS offers:

- tracking changes in your files 

- the option to revert to a previous version

- simplified collaboration on files and projects with other people


You should already have `git` installed on your Mac. To check the version, run the following command in the terminal:

`git --version`

In case you don’t have it installed, the command above will also start the installation the first time you run it.


## Terminology

**Repository** (often called _repo_) is a location where your files and folders are stored.

**Origin** is the name of the originally cloned remote repository. The name *origin* is used instead of the repository's URL for easier referencing.
 
**Main** is the name of the default branch that git creates when first creating a repository. In most cases, *main* means the *main branch*. 
Sometimes you might hear or read about the *master branch*, which is the old default branch name that you can still see in some older projects.
 
The names *main* and *origin* are a standard convention and don't have a special meaning. Although they can be renamed to whatever you want, it’s better to leave them as it is.


## Basic git commands

`git init` initializes a git repository. It can be used to create a new repository or to convert an existing directory into a git repository

`git clone` creates a local copy of a remote repository

`git branch` creates, lists or deletes branches (depending on the option it is used with)

`git add` prepares changes for commit, i.e. tells git which file(s) you want to include in the following commit

`git commit` saves the changes to your local repository. Think of it like clicking the Save button

`git status` shows the status of modified files

`git pull` updates your local files by downloading content from the remote repository. You use it when a team member has made commits to a branch on a remote repository, and you want to add those changes to your local environment

`git push` sends the changes (commits) made locally to the remote repository

`git merge` joins two or more branches together

<span style="display:block; margin-left:auto; margin-right:auto; width:95%;">![git_workflow.jpg](/img/git_workflow.jpg)</span>


## How to stage, commit and push changes

Once you have a local copy of the remote repository on your machine, you can start working on it.
The first thing you want to do is create a new line of development, that is, create a _new branch_ on which you will work (for more information on branches, check [Using Git - Advanced](https://beta.infinum.com/handbook/qa/tools/version-control-systems/using-git-advanced)). 
Afterwards, you can make the changes to your files, stage them, commit and push to the remote repository.

1. Create a **new branch** that will store your changes

	`git branch my-branch`

2. **Switch** to the newly created **branch**

	`git checkout my-branch`

3. Make the changes, e.g. edit files file1.md and file2.md

4. **Stage** the modified files
 - To stage a single file

		`git add file1.md`
 - To stage all modified files

		`git add .`

5. Check the **status** of the staged files

	`git status`

6. **Commit** the changes (with an easy-to-understand message)

	`git commit -m "Add method-abc"`

7. **Push** the changes to the remote repository

	`git push --set-upstream origin my-branch`

	`git push --set-upstream origin my-branch` configures the relationship between the remote and your local repository when you push the changes for the first time. 
Later, you can simply use `git pull` and `git push`.


This is how a complete workflow would look like:

<span style="display:block; margin-left:auto; margin-right:auto; width:80%;">![git_workflow_example.png](/img/git_workflow_example.png)</span>

## Additional resources

- [Learn GIT branching](https://learngitbranching.js.org)
- [GIT command explorer](https://gitexplorer.com)
