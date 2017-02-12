# git-repo-watcher

A simple bash script to watch a git repository and pull upstream changes if needed. 

![](https://github.com/kolbasa/git-repo-watcher/blob/images/Git-Repo-Watcher.gif)

### Configuration

There are three properties that must be set:
```Shell
REPO_NAME       # For logging purposes
DIR_TO_SYNC_IN  # The directory path of your git repository
BRANCH_TO_SYNC  # The git branch you want to keep in sync
```

### Usage

```Shell
./git-repo-watcher start
```
* Will start the script as a daemon program. All stdout und stderr will be written to a log file in the same directory as the script. The script will fail if there is already a process running.

```Shell
./git-repo-watcher stop
```
* Will stop the daemon.

```Shell
./git-repo-watcher status
```
* Tells you if the script is already running.

```Shell
./git-repo-watcher nodaemon
```
* Runs the process within the terminal's current bash instance. No logfile will be created. 

### Further information

* If you want to watch multiple repositories, just copy the script file, rename it accordingly and adjust your configuration. Do not use the same name on multiple copies.

* It also works with private repositories. At startup, the program will execute the command `git fetch` to cache you credentials with `git config --global credential.helper`.
