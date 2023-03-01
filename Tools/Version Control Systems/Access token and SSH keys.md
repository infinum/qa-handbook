> *If I was meant to be controlled, I would have come with a remote control.*

## How to generate personal access token

To make the git commands *pull* / *push* / *clone* work with two-factor authentication (2FA), you need a personal access token which you will then use for authentication when performing *clone* / *pull* / *push* operations, instead of the user password.

1. Go to *GitHub*.

2. Click the profile image and select *Settings*.

3. Select *Developer settings* in the menu on the left-hand side.

4. Select *Personal access tokens* in the menu on the left-hand side.

5. Click the *Generate new token* button.

6. Confirm your GitHub password, if prompted.

7. In the 'Note' field, type in the token name.

8. Select the *scopes* (permissions) for the access token.
 - Select *repo* to have full control of private repositories.

9. Click the *Generate token* button.

10. Make sure to copy the token because you won’t be able to see it again.

Source: [https://webkul.com/blog/github-push-with-two-factor-authentication/]()



## How to use the access token

1. Open the terminal and position to a folder in which you want to put your new project (e.g., Documents folder).

	`cd ~/Documents`

2. Clone the repository to your machine.

	`git clone https://github.com/username/repository.git`

3. Enter your GitHub *username* when prompted.

4. Don't use your GitHub password when prompted, instead enter the generated access token.

5. Wait for the cloning to finish and continue to work on the project locally.


## How to connect to GitHub using the SSH protocol and ssh-agent

By default, Git connects to remotes using the HTTPS protocol which requires you to enter your username and password every time you run a command such as *git pull* or *git push*.

Using the SSH protocol, you can connect and authenticate to remote servers and services. With SSH keys, you can connect to GitHub without supplying your username or password with each visit.

First, check whether you have any existing SSH keys. To do this, open the terminal and enter 

`ls -al ~/.ssh`

If you don't have an existing public and private key pair, then generate a new SSH key.
 
1. Open the terminal.
 
2. Create a new SSH key with the provided email as a label by running the following command (substituting in your GitHub email address):

	`ssh-keygen -t ed25519 -C "your_email@example.com"`
 
3. Press Enter when prompted to "*Enter a file in which to save the key*" to accept the default file location.
 
4. Enter a secure passphrase when prompted.
 

### How to add SSH key to ssh-agent

If you don't want to re-enter your passphrase every time you use your SSH key, you can add your key to the ssh-agent (a helper program that runs in the background while you are logged in to the system and manages your SSH keys and their passphrases).
 
1. Start the ssh-agent in the background

	`eval "$(ssh-agent -s)"`
	
	The command outputs the ssh-agent process identifier:

	`> Agent pid 59566`

2. If you're using macOS Sierra 10.12.2 or later, you will need to modify your `~/.ssh/config` file to automatically load keys into the ssh-agent and store passphrases in your keychain:

	```
	Host *
  	AddKeysToAgent yes
  	UseKeychain yes
  	IdentityFile ~/.ssh/id_ed25519
  	```

3. Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace `id_ed25519` in the command with the name of your private key file:

	`ssh-add --apple-use-keychain ~/.ssh/id_ed25519`

4. Enter the passphrase to add your identity.

5. Add the SSH key to your GitHub account (see "How to add SSH key to your GitHub account").


### How to add SSH key to your GitHub account

To configure your GitHub account to use your new (or existing) SSH key, you'll also need to add it to your GitHub account (after adding a new SSH key to your GitHub account, you can reconfigure any local repositories to use SSH).
 
1. Open the terminal and run the following command to copy the SSH key to your clipboard (make sure that you don’t copy any whitespace while copying the public key’s content):

	`pbcopy < ~/.ssh/id_ed25519.pub`

2. Open *Settings* on your GitHub page.

3. Select *SSH and GPG keys* in the menu on the left-hand side.

4. Click the *New SSH key* button.

5. In the 'Title' field type in a descriptive label for the new key. For example, if you're using your work Mac, you could call it "*work-Mac*".

6. In the 'Key' field, paste your SSH key.

7. Click the *Add SSH key* button.

8. Confirm your GitHub password, if prompted.
