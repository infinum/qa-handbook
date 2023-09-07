
A version control system is used for managing your source code. One of those systems is `git`. 

When working on a project, you most likely won't work alone but with a team. In that case, you want to make the collaboration as effortless as possible.
This is where a repository hosting service comes in handy. 

A repository hosting service is a platform used for storing your source code which you can then share with others. 
Those services are usually saved somewhere in the cloud. Besides just acting as a repository, the platforms offer additional features, such as project management and bug tracking. 

There are various hosting service solutions to choose from, some of which are:

* [GitHub](https://github.com)
* [GitLab](https://about.gitlab.com)
* [Bitbucket](https://bitbucket.org/product)
* [SourceForge](https://sourceforge.net)


## Basic workflow on GitHub

### How to create a new repository

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


### How to clone a repository 
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