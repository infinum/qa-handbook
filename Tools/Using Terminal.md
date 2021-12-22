> *I don’t care if it works on your machine! We are not shipping your machine!*

## About Terminal
Terminal, also known as _command-line_ or _console_, allows you to run commands on a computer without using a graphical user interface. You can use various commands, from simple ones for switching directories to more complex such as running scripts with multiple flags.


## How to open Terminal
Use the Spotlight search to find it.

1. Press _Cmd + Space_ on your keyboard to open the Spotlight
2. Type in _Terminal_ and hit Enter

Now add it to the Dock to reach it more easily :) 

1. Right-click on the Terminal icon in the Dock
2. Select _Options_
3. Select _Keep in Dock_


## Terminal settings
### Terminal appearance
You might want to update the appearance of your Terminal to make it a bit more readable. There are quite a few options to change the color of the background, size and color of the text, cursor, and so on.

1. Open Terminal
2. Click Terminal in the toolbar 
3. Select Preferences 
4. Select the Profiles tab 
5. Select the Text tab

## Change Terminal behavior
There are also various options to edit the Terminal behaviour, spread across multiple tabs: Window, Tab, Shell, Keyboard, Advanced.

For example, under the _Shell_ tab you can specify the command that is run on startup:

1. Select the Shell tab under Profiles 
2. Select the _Run command_ checkbox 
3. In the input field type in the command you wish to run, for example:
  - `cd /Users` to open the Terminal positioned to the Users directory
  - `echo $$` to run the `echo` command as soon the Terminal is open
	

Another interesting option is to close the Terminal window when the shell exits. This can be useful when you run shell commands from your project and don’t want to leave the Terminal open. 

1. Select the Shell tab under Profiles
2. From the dropdown in _When the shell exits_ select _Close the window_ option
   - if you run the `exit` command, the Terminal window will close


## Terminal alternatives
The Terminal is not the only app for using the command line on the Mac. There are various alternatives such as iTerm2, Hyper, Upterm, Alacritty and ZOC, to name a few.
Each of these comes with some differences when compared to the Terminal, often adding additional features.

## Shell
A shell is a computer program that basically allows you to control your computer. You can use it to control other programs, interact with the system, or simply automate repetitive tasks. The commands can be entered directly, or read from a file called the shell script.

To access a shell you need an app that runs it, such as Terminal/iTerm2 on Mac or Command Prompt/GitBash on Windows.

There are various shell programs to choose from, like sh, bash, ksh, tcsh and zsh.

- **sh** or Bourne Shell 
  - the original shell still used on UNIX systems
  - very basic with a few features

- **bash** or Bourne Again Shell
  - the [GNU Project’s](https://www.gnu.org/home.en.html) shell
  - it's compatible with _sh_, meaning commands that work in _sh_ also work in _bash_ (vice-versa is not always the case)
  - provides additional features and improvements over _sh_

- **zsh** or Z-shell
  - extended version of _sh_, including some _bash_ features 
  - quite similar to _bash_ but with some improvements and more customizable
  - commands that work in _bash_ work in _zsh_


## Command line arguments
When reading about command-line arguments, you might come across terms like _flag_, _switch_, _option_, _argument_, _parameter_, and so on, which are often used interchangeably. 
Arguments tell the process or function to perform a different operation depending on its value. Arguments are often used in command-line programs, and they are basically options that change the behaviour of a program.

There are a couple of types of arguments:

- Arguments that take a value
- Arguments that don’t take a value
- Positional arguments

Arguments can start with a single dash (-) or a double dash (--).

A **flag** argument usually refers to a boolean argument that by including it, it changes the behaviour of a program. If you include a flag argument its boolean value is set to true, if not, it is set to false. 
For example, 

`~ ls ` 

lists all visible files and folders in the current folder, but if we add a flag -a, making it

`~ ls -a`

it lists all visible and invisible files and folders.

Another example, in the following command: 

`python test.py --report `

the `--report` is a flag which tells the process to include / activate the report option. 
With `--report` flag included a report is generated once the test is run, otherwise, if not included, the report is not generated.

Arguments that start with a double dash (--) often take an argument themselves. For example, in a Python script we might have an env flag that uses a different environment depending on the value we specify when including the `--env` argument:

`python test.py --env=test_environment`
`python test.py --env=staging_environment`

For more details on arguments, read this [blog post](https://betterdev.blog/command-line-arguments-anatomy-explained/).


## List of useful commands
The following list of commands works in the Terminal but might not work in other similar apps.

### Directory / Folder navigation
Position to a directory, e.g. Code folder inside the Documents folder

`➜  ~  cd Documents/Code`

Go back to the directory above the current one

`➜  ~  cd ..`

Go back to the root (Home) directory

`➜  ~  cd`

### Permissions
Change the file permission to executable

`➜  ~ chmod +x /path/to/file`

### Echo
Get process ID (PID) of the current terminal / tab

`➜  ~  echo $$`

### List files and folders
List all visible  files and folders in the current folder

`➜  ~ ls`

List all visible and invisible files and folders in the current folder

`➜  ~ ls -a`

List all visible files and folders in the current folder with permissions

`➜  ~ ls -l`

### lsof
List all open files and processes

`➜  ~ lsof`

Check which software uses which port

`➜  ~ lsof -n -i4TCP`

List open files and processes with PID 66460

`➜  ~ lsof -p 66460`

### Open file / directory
Open a directory, e.g. Documents

`➜  ~  open Documents`

Open a file inside Documents directory

`➜  ~  open Documents/file_name.txt`

Open zsh resource file

`➜  ~  open ~/.zshrc`

### ps
Displays your and other users' processes

`➜  ~ ps -ax `

Display processes that contain “Finder”

`➜  ~ ps -ax | grep Finder`

### Print Working Directory
Display the path to the current / working directory

`➜  ~  pwd`

### Close / Quit terminal
Quit Terminal

`➜  ~  exit`

Quit Terminal right after running a command

`➜  ~  python some_script.py; exit`

### System info
Get system name

`➜  ~ id -un`

Get hostname

`➜  ~ hostname`

Display system information (long version)

`➜  ~ system_profiler`

Display system information (short version)

`➜  ~ system_profiler -detailLevel mini`

###  Networking
View a list of all active devices on a local network

`➜  ~ arp -a`


---

![dogbert_terminal.png](/img/dogbert_terminal.png)
