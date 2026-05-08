> *If I was meant to be controlled, I would have come with a remote control.*

## How to generate a personal access token

If your GitHub account uses two-factor authentication (2FA), Git commands such as *clone*, *pull*, and *push* cannot use your GitHub password.

Instead, generate a personal access token and use it as your password when Git asks you to authenticate.

1. Go to *GitHub*.

2. Click the profile image and select *Settings*.

3. Select *Developer settings* in the menu on the left-hand side.

4. Select *Personal access tokens* in the menu on the left-hand side.

5. Click the *Generate new token* button.

6. Confirm your GitHub password, if prompted.

7. In the 'Note' field, enter a name for the token.

8. Select the *scopes* (permissions) for the access token.
	- Select *repo* to have full control of private repositories.

9. Click the *Generate token* button.

10. Copy the token immediately. You won’t be able to see it again after you leave the page.

Source: [https://webkul.com/blog/github-push-with-two-factor-authentication/]()



## How to use the access token

1. Open the terminal and go to the folder where you want to put the project. For example:

	`cd ~/Documents`

2. Clone the repository to your machine.

	`git clone https://github.com/username/repository.git`

3. Enter your GitHub *username* when prompted.

4. When Git asks for a password, enter the generated access token instead of your GitHub password.

5. Wait for the cloning to finish and continue to work on the project locally.


## How to connect to GitHub using the SSH protocol and ssh-agent

By default, Git connects to remote repositories using HTTPS. With HTTPS, Git may ask for your username and password when you run commands such as *git pull* or *git push*.

SSH lets you authenticate with a key instead. After you set up SSH keys, you can connect to GitHub without entering your username or password each time.

First, check whether you already have SSH keys. Open the terminal and run:

`ls -al ~/.ssh`

If you don't have an existing public and private key pair, generate a new SSH key.
 
1. Open the terminal.
 
2. Create a new SSH key with your GitHub email address:

	`ssh-keygen -t ed25519 -C "your_email@example.com"`
 
3. When prompted to "*Enter a file in which to save the key*", press Enter to accept the default file location.
 
4. Enter a secure passphrase when prompted.
 

### How to add SSH key to ssh-agent

If you don't want to enter your passphrase every time you use your SSH key, add the key to ssh-agent.

ssh-agent is a helper program that runs in the background and manages your SSH keys and passphrases.
 
1. Start ssh-agent in the background:

	`eval "$(ssh-agent -s)"`
	
	The command outputs the ssh-agent process identifier:

	`> Agent pid 59566`

2. Update your `~/.ssh/config` file so your key loads automatically and the passphrase is stored in your keychain.

	Open the config file:

	`open ~/.ssh/config`

	Add this content to the file:

	```
	Host *
  	AddKeysToAgent yes
  	UseKeychain yes
  	IdentityFile ~/.ssh/id_ed25519
  	```

3. Add your SSH private key to ssh-agent and store the passphrase in the keychain. If your key has a different name, replace `id_ed25519` with your private key file name:

	`ssh-add --apple-use-keychain ~/.ssh/id_ed25519`

4. Enter the passphrase to add your identity.

5. Add the SSH key to your GitHub account. See "How to add SSH key to your GitHub account".


### How to add SSH key to your GitHub account

Add the SSH key to your GitHub account settings to authorize your machine. After that, update your local repository remotes to use SSH.
 
1. Open the terminal and copy the SSH key to your clipboard:

	`pbcopy < ~/.ssh/id_ed25519.pub`

2. Open *Settings* on your GitHub page.

3. Select *SSH and GPG keys* in the menu on the left-hand side.

4. Click the *New SSH key* button.

5. In the 'Title' field, enter a descriptive label for the new key. For example, if you're using your work Mac, you could call it "*work-Mac*".

6. In the 'Key' field, paste your SSH key.

7. Click the *Add SSH key* button.

8. Confirm your GitHub password, if prompted.
