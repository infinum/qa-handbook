## What is pyenv

`pyenv` is a tool used to manage multiple Python versions on a single system. It helps to easily install, switch between, and manage different versions of Python.


## Why use it

* **Avoid version conflicts**: Different projects may require different versions of Python. `pyenv` allows you to manage and isolate these versions, so you don’t run into compatibility issues.

* **Easier testing**: You can test your code across multiple versions of Python without installing each version system-wide.

* **Better control**: You can manage Python versions independently of the system's default Python, preventing changes that could affect system tools or applications that rely on a specific version of Python.


## Before you continue with pyenv installation

Make sure [Homebrew](https://brew.sh/) is installed in the correct location. 
If you have migrated from Mac using Intel architecture to one with ARM, you might have Homebrew still installed in the old location.

Run: `which brew`

Expected output: `/opt/homebrew`

If your output is `/usr/local`, you should re-install Homebrew.


## How to install pyenv

1. Install dependencies

    ```sh
    ➜  ~ brew install openssl readline sqlite3 xz zlib tcl-tk@8
    ```

2. Install pyenv using [pyenv-installer](https://github.com/pyenv/pyenv-installer)
    * This should install `pyenv` and a few useful plugins like `pyenv-virtualenv`

    ```sh
    ➜  ~ curl https://pyenv.run | zsh
    ```

3. Update PATH in `/.zprofile`. Add the following:

    ```
        export PYENV_ROOT="$HOME/.pyenv"
        [[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
        eval "$(pyenv init --path)"
        eval "$(pyenv init -)"
        eval "$(pyenv virtualenv-init -)"
    ```

4. Restart the terminal


## How to install Python using `pyenv`

1. Run the following to check available CPython versions:

    ```sh
    ➜  ~ pyenv install --list
    ```

    * This returns quite a few, including Python 2

    ```sh
    ➜  ~ pyenv install --list | grep -E '^  3\.[0-9]+'
    ```
        
    *  This returns a list of available CPython 3 versions

2. Install a specific Python version, e.g. 3.11.11:

    ```sh
    ➜  ~ pyenv install -v 3.11.11
    ```


### Where is Python installed

Each version is installed in pyenv root directory.

To check all installed versions, run: `ls ~/.pyenv/versions/`


## How to set Python version

### Check available versions

Run `pyenv versions` to see which versions you have available.
The `*` indicates which version is currently active. By default it is the system's version.

```sh
➜  ~ pyenv versions
    * system (set by /Users/username/.pyenv/version)
    3.9.7
    3.11.11
```

### Set system Python version

To switch the version you want to use for the system, use the `global` command. 

```sh
➜  ~ pyenv global 3.11.11
    system
    3.9.7
    * 3.11.11 (set by /Users/username/.pyenv/version)
```

Run `python -V` to check if the correct version is applied.

```sh
➜  ~ python -V
Python 3.11.11
```

To change it back to default system version

```sh
➜  ~ pyenv global system
```

## How to uninstall a particular Python version

You can uninstall a Python version using pyenv uninstall, or simply delete the directory to remove a specific Python version.

**Uninstall:**

```sh
➜  ~ pyenv uninstall 3.11.11
```


**Remove:**

```sh
➜  ~ rm -rf ~/.pyenv/versions/3.11.11
```

## How to set virtual environment with pyenv

`pyenv` is primarily a tool for managing Python versions. But it also supports plugins.
One of those supported plugins is `pyenv-virtualenv`, which helps you manage virtual environments for specific Python versions.

### Create virtual environment

When creating a virtual environment, try to use a name that would easily associate it with the project you are working on. Just to make things convenient. 

```sh
➜  ~ pyenv virtualenv 3.11.11 my_project_venv
```

### Activate virtual environment

```sh
➜  ~ pyenv local my_project_venv
```

This creates a `.python-version` file in the current working directory, which automatically activates the virtual environment whenever you are in that directory.

```sh
➜  ~ pyenv which python
/Users/username/.pyenv/versions/my_project_venv/bin/python
```

### Remove virtual environment

To remove the local version setting, you can do one of the following:

Delete the `.python-version` file in your directory:

```sh
➜  ~ rm .python-version
```

Or use the `--unset` command to remove the local version setting:

```sh
➜  ~ pyenv local --unset
```

Once the `.python-version` file is removed or reset, the system will use the global Python version.


### Additional resources

[pyenv] https://github.com/pyenv/pyenv
[Managing Multiple Python Versions With pyenv](https://realpython.com/intro-to-pyenv/)
