# git-repo-watcher

A simple bash script to watch a git repository and pull upstream changes if available.

### Usage

This will start a watcher, that looks for changes every 10 seconds:
```bash
./git-repo-watcher -d "/path/to/your/repository"
```

The time interval can be changed by passing it to `-i`:
```bash
./git-repo-watcher -d "/path/to/your/repository" -i 60 #seconds
```

You can add your own logic to the file `git-repo-watcher-hooks`.
For example, you can then start your build process in case of changes:

```bash
# $1 - Git repository name
# $2 - Branch name
# $3 - Commit details
change_pulled() {
    echo "Starting build for commit: $@"
    ./your-build-script.sh
}
```

If you have more than one repository, you can pass a copy of the `git-repo-watcher-hooks` file like so:
```bash
./git-repo-watcher -d "/path/to/your/repository" -h "/path/to/your/hooks-file"
```

### Private repositories

The script works for private repositories.
First configure a password cache with `git config --global credential.helper "cache --timeout=60"`.
Make sure that the `timeout` is greater than the time interval given to the script. Both are given as seconds.

At startup, the program will execute `git fetch` and ask for your credentials.

If you want it to run in the background as a daemon process, you have to execute `git fetch` beforehand.
For example:

```bash
cd "/path/to/your/repository"
git config --global credential.helper "cache --timeout=60"
git fetch

# Checking exit code
if [[ $? -eq 1 ]]; then
    echo "Wrong password!" >&2
    exit 1
fi

# Disown process
git-repo-watcher -d "/path/to/your/repository" > "/path/to/your/logfile.txt" &
```

### Notes

* Make sure your local repository is tracking a remote branch, otherwise the script will fail.
* The test suite `git-repo-watcher-tests` is using the test framework `shunit2`, it will be downloaded automatically to your `/tmp` folder.
