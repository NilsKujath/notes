# Notes on Git and it's interaction with GitHub

## Git Basics

### Committing

`git init` turns a local directory into a Git repository.
A file in a Git repository is either *tracked* or *untracked*.
`git add <untracked_file>` tracks a previously untracked file.

A tracked file is either *modified*, *staged*, or *committed*.
Only staged files are part of the next commit.
`git add` stages a (modified) file for commit.
`git commit` commits all files that are in the *staging area*.

`git status` shows the state the files in a directory are in.
`git add <file>` adds the specified file to the staging area.
To already add the commit message with the commit command, type:
`$ git commit -m "message"` adds the commit message with the commit command.

`git commit -a` stages all unstaged files and commits.
Commands can be shortened by setting aliases.
Git settings are defined at three levels: system, global (user), and local (specific repository).
The more specific settings override the less specific ones.
`git config --list --show-origin` displays each setting and the level of its origin.

Practical aliases:
`git config --global alias.cm 'commit -m'`
`git config --global alias.cam 'commit -a -m'`

### .gitignore File 

Files that are in the directory but should be ignore by Git can be defined in a file named `.gitignore` that can be created inside the directory.
`#` is used to comment inside .gitignore file.
`*.pdf` igonores all .pdf files.
`dir/**/*.pdf` ignores all .pdf files in directory dir and all its subdirectories.

### Git Log & Tagging Release Points

`git log` list all commits made in the current repository.
`$ git log --decorate --all --oneline --graph`

Practical aliases:
`$ git config --global alias.l 'log --decorate --all --oneline --graph'`

Certain release points can be marked with tags.
`git tag` list all existing tags.
Git distinguishes between *leightweight* and *annotated* tags.
An annotated tag is created as follows:
`$ git tag -a v1.0 -m "message"`
Tags need to be explicitly pushed to a remote server (more below).

### Working with Remotes

`git clone <remote_url>` creates a local copy of specified remote repository.
`git remote add <remote_url>` adds remote.
`git push <remote> <remote_branch_name>` (usually `origin master`) pushes up to remote you have write access to.
`git fetch <remote>` (usually named `origin`) updates local database from remote.

Practical aliases:
`git config --global alias.pom 'push origin master'`

### Squasing the last *n* commits
Run `git rebase --interactive HEAD~n` (where *n* indicates how many commits from your history should be rebased).
This will open an editor that displays the options for rebasing.
To meld a newer commit into an older one, change `pick` to `squash` for the newer commit and close the editor.
A new editor opens for editing the commit message.

### Branching and Merging
`git branch <branch_name>` creates a new branch (a new pointer to the last commit on the branch you are currently on).
`git log --decorate` shows you which branch you are currently on.
`git checkout <branch>` lets you switch to an existing branch.
`git log` only shows you the commit history below the branch you are currently checking out (unless you add --all).

`git merge <branch>` merges the named branch with the current branch (to make sure to be on the right branch: `git checkout <branch>`).
If there is no divergent work to merge together, git treats it as fast-forewarding the commit history.
After a branch is no longer useful, it can be deleted by `git branch -d <branch>`.

`git branch` lists all branches (`*` indicates the branch you currently checked out, adding `-v` show the last commit message for each branch).

## Thoughts on Workflow

### GitHub Flow Workflow

GitHub Flow employs two kinds of branches:
- `master`: anything on master is deployable.
- `feature*` or `hotfix*`: any new feature or hotfix is build on a descriptively named branch.
Before a `feature*` branch is merged with `master` the merge conflicts should be solved on the `feature*` branch.
This is done by merging the `master` branch into the `feature*` or `hotfix*` branch via `git merge master` before merging the `feature*` or `hotfix*` branch into `master`.
