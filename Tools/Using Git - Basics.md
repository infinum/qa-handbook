> *Fellow testers, we cannot not to find bugs.*

## Git and GitHub

### What is Git?
Git is a **Version Control System** (VCS). There are various version control systems, but Git is by far the most popular one, both for individual and company use. On a very basic level, there are a couple of awesome things a VCS offers:

 - tracking changes in your files 

 -  the option to revert to a previous version

 - simplified collaboration on files and projects with other people


You should already have Git installed on your Mac. To check the version, run the following command in the terminal:

`git --version`

In case you don’t have Git installed, the command above will also start the installation the first time you run it.


### What is GitHub?
GitHub is a cloud-based Git repository hosting service, i.e. a web-based Git repository. GitHub provides:

 - a free and easy place to use Git

 - a cloud to store your code in

 - various features for easier collaboration with other people


## Terminology
**Repository** (often called ‘repo’) is a location where your files and folders are stored.

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



## Basic workflow
The sections below show the steps for a basic git workflow when starting a project from scratch - from creating a remote repository, cloning it to your machine, and then pushing the changes made locally to the remote repository.

### How to create a new GitHub repository
The following steps will help you create an initialized GitHub repository with a README file included. By default, GitHub creates a single branch named *main*. 

1. Log in to **GitHub**

2. Click the **+** button next to your profile image and select **New repository** 

3. Type in the repository name

4. Choose the **visibility** of the repository by selecting *Public* or *Private*
 - *Public* repositories are visible to everyone so think twice before pushing anything to it
 - *Private* repositories are only accessible to you and the people you share them with

5. In the *Initialize this repository with* section, select the **Add a README file** checkbox
 - It is a good idea to include a README file containing information about the project

6. Click the **Create Repository** button


### How to clone a GitHub repository 
Cloning a GitHub repository creates a local copy of that remote repository. The following steps show how to clone a remote repository and create an initialized local repository on your machine.

1. Go to **GitHub** and open the repository’s page

2. Click the **Code** button to expand the dropdown menu 

3. Select the desired option, e.g. SSH, and **copy** the **URL**
	- **NOTE**: If you already have 2FA enabled and try to clone the repository using the HTTPS option, you might run into the '*Authentication failed*' issue 

4. Open the terminal on your machine and position to a folder in which you want to put your new project (e.g. Documents folder)

	`cd ~/Documents`

5. **Clone** the repository to your machine
	
	`git clone git@github.com:username/repository.git`
	
6. When prompted, enter your GitHub **username** / **password** or passphrase, depending on the selected cloning option (HTTPS or SSH)

7. **Change** the current working directory to the newly created **directory**

	`cd repository`


### How to stage, commit and push changes
Once you have a local copy of the remote repository on your machine, it is time to start working on it. The first thing you want to do is to create a new line of development, that is, create a new branch to store your changes (for more information on branches, check Using Git - Advanced). Afterwards, you can make the changes to your files, stage them, commit and push to the remote repository.

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

7. **Push** the changes to the remote GitHub repository

	`git push -u origin my-branch`

	`git push -u origin main` configures the relationship between the remote and your local repository when you push the changes for the first time. 
Later, you can simply use `git pull` and `git push`


This is how a complete workflow would look like:

<span style="display:block; margin-left:auto; margin-right:auto; width:80%;">![git_workflow_example.png](/img/git_workflow_example.png)</span>

---

![dilbert-git-basics.png](/img/dilbert-git-basics.png)
