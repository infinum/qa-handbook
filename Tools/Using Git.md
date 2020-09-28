> *You can see a lot by just looking.*

## Git and GitHub

### What is Git?
Git is a Version Control System (VCS). On a very basic level, there are two awesome things a VCS allows you to do:

* You can track changes in your files
* It simplifies working on files and projects with multiple people

There are multiple Version Control Systems, but Git is by far and large the most popular — both for individual and company use.

You should already have Git installed on your Macbook. If not, just run in Terminal:

`git --version`

### What is Github?

On the other hand, GitHub is a web based Git repository.

* It provides a free and easy place to use Git
* It provides the cloud to store your code in
* It allows you to interact with other developers

### Make “git pull/push/clone” work with two factor authentication

2FA requires user access token instead of the user password while running pull and push operation.

First is needed to generate new Personal access token.

This can be done by clicking on a profile photo (Github profile) and then Settings. Find Developer settings in a left-hand side menu and click on it. Then click on Personal access tokens. 

Now you can Generate new token and use that token to clone the qa-handbook-private repository locally.

Source: [https://webkul.com/blog/github-push-with-two-factor-authentication/]()

### How to clone the repository

1. Open Terminal
2. Type in a command below:

	`git clone https://github.com/infinum/qa-handbook-private.git`
		
3. You will be asked to enter your username (You can find out what is your username by clicking on the profile photo, you will see "Signed in as XY"

4. You will be asked to enter your password. Do not enter your Github password, instead enter the token you generated in earlier steps.


5. Wait until the cloning is finished.


Now that you have repository locally on your Macbook, you don't need Github anymore, now you can update QA Handbook locally through Terminal.

**Steps necessary for pushing the changes:**

1. Position to your working directory:

	`cd qa-handbook-private`
		
	I will update the section "How to update this Handbook" so I need to navigate to the folder in which this file is saved.
	
	And because I'm not sure where this file is hiding. I will use the commands below:
		
	`ls` - list the files in the current working directory
	
	`open` - open the file and make changes
	
	![](/img/some_commands.png)
	
2. Make changes to the file you want

3. Let's check the status and see what happened after we made changes to the file. Use command below:

	`git status`
		
	![](/img/file_update.png)
		
4. Propose changes using:

	`git add <filename>`
	
	If you made changes on multiple files and want to push all those changes at once, use:
	
	`git add .` 

5. To actually commit these changes use:

	`git commit -m "Commit message"`
	
	Now the file is commited but it's not pushed yet. 
	
6. Changes are now on your local working copy. To send those changes to remote repository, execute:

	`git push origin master`
		
Great! Now the changes are visible in the QA Handbook.

Now check out these slides [on updating the Handbook](https://drive.google.com/file/d/1SH0Hoz7j_OzmTtgJTJ-vi-yjH1xtv4Ix/view?usp=sharing).

### Connecting to Github with SSH and SSH-AGENT

By default Git connects to remotes using the HTTPS protocol, which requires you to enter username and password every time you run a command such as git pull or git push.

Using the SSH protocol, you can connect and authenticate to remote servers and services. With SSH keys, you can connect to GitHub without supplying your username or password at each visit.

First, check if you have any existing SSH keys. You can do this by opening Terminal, and enter `ls -al ~/.ssh`

If you don't have an existing public and private key pair, then generate a new SSH key.

1. Open Terminal

2. Paste the text below, substituting in your GitHub email address.

	`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
	
	Above command creates a new ssh key, using the provided email as a label

3. When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

4. At the prompt, type a secure passphrase.

If you don't want to reenter your passphrase every time you use your SSH key, you can add your key to the SSH agent - a program that runs in background while you are logged in to the system and stores your keys in memory, manages your SSH keys and remembers your passphrase. 

But before adding a new SSH key to the ssh-agent you need to have an existing SSH key (if you don't have one, generate a new SSH key by following the steps above)

1. Start the ssh-agent in the background.

	`eval "$(ssh-agent -s)"`

	That command outputs the ssh-agent process identifier:
	
	`> Agent pid 59566`
	
2. If you're using macOS Sierra 10.12.2 or later, you will need to modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain.

	```
	Host *
  	AddKeysToAgent yes
  	UseKeychain yes
  	IdentityFile ~/.ssh/id_rsa
  	```
3. Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_rsa in the command with the name of your private key file.

	`ssh-add -K ~/.ssh/id_rsa`
	
4. Enter the passphrase and your identity will be added.

5. Add the SSH key to your GitHub account bt following the steps below.

To configure your Github account to use your new (or existing) SSH key, you'll also need to add it to your GitHub account (after adding a new SSH key to your GitHub account, you can reconfigure any local repositories to use SSH).

1. Copy the SSH key to your clipboard by pasting below command in Terminal:

	`pbcopy < ~/.ssh/id_rsa.pub`
	
	Be sure that you don’t copy any whitespace while copying public key’s content
	
2. Now go to your Github page, in the upper-right, click your profile photo, then click Settings.

3. In the user settings sidebar, click SSH and GPG keys.

4. Click New SSH key or Add SSH key.

5. In the "Title" field, add a descriptive label for the new key. For example, if you're using a work Mac, you might call this key "Work MacBook".

6. Press `Command + V` to paste your key into the "Key" field.

7. Click Add SSH key.

8. If prompted, confirm your GitHub password.

Now your SSH key is added to your GitHub account.

---

![how-to-update-this-handbook.png](/img/how-to-update-this-handbook.png)
