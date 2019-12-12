#!/usr/bin/env bash

# $1 - Git repository name
# $2 - Branch name
startup() {
    echo "Watch started: $*"
}

# $1 - Git repository name
# $2 - Branch name
no_changes() {
    echo "Nothing changed: $*"
}

# $1 - Git repository name
# $2 - Branch name
# $3 - Commit details
change_pulled() {
    echo "Changes pulled: $*"
}

# $1 - Git repository name
# $2 - Branch name
# $3 - Commit details
pull_failed() {
    echo "Pull failed --> Exiting: $*"
    exit 1
}

# $1 - Git repository name
# $2 - New branch name
# $3 - Old branch name
branch_changed() {
    echo "Branch changed: $*"
}

# $1 - Git repository name
# $2 - Branch name
upstream_not_set() {
    echo "Upstream not set: $*"
}

# $1 - Git repository name
# $2 - Branch name
local_change() {
    echo "local file changed: $*"
}

# $1 - Git repository name
# $2 - Branch name
diverged() {
    echo "Diverged --> Exiting: $*"
    exit 1
}
