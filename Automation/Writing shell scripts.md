
## What are shell scripts

[Shell](https://infinum.com/handbook/qa/tools/using-terminal#shell) scripts are programs consisting of a series of commands in a file. 

Instead of typing various commands into the Terminal one by one, you can execute them all by running the script.

With a shell script you can automate repetitive tasks to do them easily and more accurately.


## bash or zsh

`bash` is the default shell for many Linux distributions and was also the default command-line interpreter for Mac on macOS Mojave and earlier versions.

Newer versions of macOS (Catalina and later) use `zsh` as the default shell.
 
`zsh` is an extended version of `sh` and includes some `bash` features. Most commands, control structures and syntax from `bash` work in `zsh` as well.

### Install zsh

If your default shell is `bash`, and you wish to switch to `zsh`, install [oh-my-zsh](https://ohmyz.sh/).

Or using Homebrew: `$ brew install zsh`

#### Check path to the zsh binary

Once you have `zsh` installed, check the path to the binary by running:

`$ which zsh`

Output: `/usr/bin/zsh`

## Writing a zsh script

### Create a new file

Start working on your script by creating a new file by using a text editor.

Or using a command-line interface: `$ touch script_name.zsh`

The extension for `bash` scripts is `.sh`. The same extension can be used for the `zsh` scripts as well. The extension is not necessary but will help you identify the file more easily. You can also change the file extension for your zsh scripts from `.sh` to `.zsh`.

The file extension has no effect on the interpreter used for executing the script. The interpreter is determined by the _shebang_.

### Shebang

The first line of a shell script is the so-called _shebang_ character sequence. This line indicates which interpreter to use when running the script.

`#!/bin/zsh`

The shebang consists of the following sequence:

- `#!` - tells the program to load an interpreter to read the code

- `/bin/zsh` - the path to the zsh interpreter


### Adding comments

You are encouraged to use comments in your scripts. The comments start with the # character and will not be executed. They will, however, help with the code readability.

    #!/bin/zsh
    # Say “Hello” to the world


### Adding code

Once you have the shebang and the comment in place, add some code to be executed.
For starters, say “Hello” to the world when the script is executed. 

The command used for printing the string: `echo`

    #!/bin/zsh
    # Say “Hello” to the world
    
    echo Hello world!


## Executing a ZSH script

Execute the script by providing the full file path to the script. 
When running the script, the first argument specifies the interpreter you want to use.
For example, if the file is in the Documents folder, run the following command to execute the script using `zsh`:

`$ zsh Documents/script_name.zsh`

Executing a script that accepts arguments:

`$ zsh Documents/script_name.zsh <arg1> <arg2> <argN>`

Execute the script by providing a relative path to the script:

`$ zsh ./script_name.zsh <arg1> <arg2> <argN>`


### Permission denied 

If you run your script and get the zsh: permission denied error, you will need to modify the file permissions. The permission can be updated for the file or the entire folder.
To set _execute_ permissions for the shell script, use the `chmod` command:

`$ chmod +x script_name.zsh`


## Adding variables to the script 

Define a variable:

`variable_name=value`

To get the value of the variable, add the $ character before the variable name:

`$variable_name`

    #!/bin/zsh
    # Say “Hello” to John
    
    greeting=Hello
    name=John
    
    echo $greeting $name


## Adding parameters (flags) to the script 

You can add parameters (flags) to the script to modify its behaviour by passing arguments.
This is done using the built-in shell command for parsing command-line arguments `getopts`.

The `getopts` command is added inside a while loop so that all options are parsed. 
Right after the `getopts` keyword, we define the options our script accepts. In this case the options are name (`n`) and age (`a`).
The `OPTARG` refers to the corresponding value passed to the script.

    #!/bin/zsh
    # Say “Hello” to the user
    
    greeting=Hello
    
    while getopts n:a: flag
    do
        case "${flag}" in
            n) name=${OPTARG}
            echo "Name set to: $name";;
            a) age=${OPTARG}
            echo "Age set to: $age";;
        esac
    done
    
    echo "$greeting $name ($age)"

**Executing the script**

The script is executed by providing the interpreter, path to the script and then the arguments.
The arguments are provided by firstly specifying the argument starting with a _hyphen_ (e.g. `-n`) and then its value, separated with a single space.

`zsh ./test_input.zsh -n John -a 25`


**Output:**

    Name set to: John
    Age set to: 25
    Hello John (25)

## Additional resources

[bash cheatsheet](https://devhints.io/bash)

[zsh cheatsheet](https://devhints.io/zsh)

[Command line arguments in scripts](https://www.baeldung.com/linux/use-command-line-arguments-in-bash-script)

[Positional parameters in scripts](https://linuxcommand.org/lc3_wss0120.php)

[Using flag arguments](https://linuxconfig.org/bash-script-flags-usage-with-arguments-examples)


---

![dilbert_writing_shell_scripts.png](/img/dilbert_writing_shell_scripts.png)

*Image downloaded from [dilbert.com](https://dilbert.com/strip/2022-06-05): 05-06-22 by Scott Adams*
