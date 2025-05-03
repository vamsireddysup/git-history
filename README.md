# Git Commands Documentation

This README documentation serves as my personal reference and might help collaborators understand my workflow.
## Table of Contents
- [Repository Setup](#repository-setup)
- [Basic Git Commands](#basic-git-commands)
- [Branching and Merging](#branching-and-merging)
- [Remote Repository Operations](#remote-repository-operations)
- [Configuration Commands](#configuration-commands)
- [GPG Signing](#gpg-signing)
- [Miscellaneous Commands](#miscellaneous-commands)

## Repository Setup

### Initialize a New Repository
```bash
git init
```
Creates a new Git repository in the current directory, establishing the foundation for version control.

### Clone a Repository
```bash
git clone git@github.com:username/repository-name.git
```
Creates a local copy of a remote repository, downloading all files and history.

## Basic Git Commands

### Check Repository Status
```bash
git status
```
Displays the state of the working directory and staging area, showing which changes have been staged and which files aren't being tracked.

### View Commit History
```bash
git log
```
Shows the chronological commit history for the repository, displaying commit hashes, authors, dates, and messages.

```bash
git log HEAD..origin/master --oneline
```
Shows commits that exist in the remote 'origin/master' branch but not in your current branch in a compact format.

### Add Files to Staging
```bash
git add .
```
Adds all modified and new files in the current directory to the staging area, preparing them for commit.

```bash
git add specific_file
```
Adds only the specified file to the staging area.

### Commit Changes
```bash
git commit -m "Commit message"
```
Records the staged snapshot permanently in version history with a descriptive message.

```bash
git commit -S -m "Message"
```
Creates a commit with a GPG signature for verification, enhancing security.

## Branching and Merging

### List Branches
```bash
git branch
```
Lists all local branches in the repository, marking the current branch with an asterisk.

```bash
git branch -a
```
Lists both local and remote-tracking branches, providing a complete view of all branches.

```bash
git branch -r
```
Lists only the remote-tracking branches, showing what exists on the remote repositories.

### Create and Switch Branches
```bash
git checkout -b branch_name origin/branch_name
```
Creates a new branch based on a remote branch and switches to it immediately.

### Delete a Branch
```bash
git branch -d branch_name
```
Deletes a branch after its changes have been merged, preventing deletion of unmerged branches.

### Rename a Branch
```bash
git branch -m new_name
```
Renames the current branch to the specified new name.

### Merge Branches
```bash
git merge branch_name
```
Incorporates changes from the specified branch into the current branch.

### Rebase
```bash
git rebase --continue
```
Continues a rebase operation after resolving conflicts, applying commits one by one onto the target branch.

## Remote Repository Operations

### Add Remote Repository
```bash
git remote add origin git@github.com:username/repository-name.git
```
Creates a connection to a remote repository, giving it the name "origin".

### Change Remote URL
```bash
git remote set-url origin git@github.com:username/repository-name.git
```
Updates the URL of an existing remote repository, useful when switching between HTTPS and SSH.

### View Remote Information
```bash
git remote -v
```
Lists all remote connections along with their URLs, showing both fetch and push destinations.

```bash
git remote show origin
```
Displays detailed information about a specific remote, including tracked branches and local configuration.

### Push to Remote
```bash
git push origin branch_name
```
Sends local commits to the remote repository's branch.

```bash
git push -u origin branch_name
```
Pushes and sets the upstream reference, linking local and remote branches for simpler future commands.

```bash
git push -f origin branch_name
```
Forces the push even if it results in a non-fast-forward merge. Use with caution as it can overwrite remote changes.

### Delete Remote Branch
```bash
git push origin --delete branch_name
```
Removes a branch from the remote repository, useful for cleaning up after merging.

### Pull from Remote
```bash
git pull origin branch_name
```
Fetches changes from the remote repository and merges them into the current branch.

```bash
git pull --rebase origin branch_name
```
Fetches remote changes and replays your local commits on top of them instead of creating a merge commit.

```bash
git pull --no-rebase origin branch_name
```
Explicitly performs a merge (not rebase) when pulling, creating a merge commit.

```bash
git pull origin branch_name --allow-unrelated-histories
```
Allows merging branches that don't share a common ancestor, useful when combining projects.

### Fetch from Remote
```bash
git fetch origin
```
Downloads objects and refs from the remote without merging, allowing inspection before integration.

## Configuration Commands

### Set User Configuration
```bash
git config --global user.signingkey KEY_ID
```
Sets the GPG key used for signing commits and tags globally for all repositories.

### Set Default Behavior
```bash
git config --global color.ui auto
```
Enables colorized output in the terminal for better readability.

```bash
git config --global init.defaultBranch master
```
Sets the default branch name for new repositories to "master" instead of Git's default.

## GPG Signing

### Enable Commit Signing
```bash
git config --global commit.gpgsign true
```
Configures Git to automatically sign all commits with your GPG key, enhancing security.

```bash
git config --global tag.gpgSign true
```
Ensures all tags are GPG signed for verification and integrity.

### Unset GPG Format
```bash
git config --global --unset gpg.format
```
Removes a previously set GPG format configuration, reverting to the default behavior.

## Miscellaneous Commands

### Remove Files from Git
```bash
git rm file_path
```
Removes files from both the working directory and the index, staging the deletion for the next commit.

### Check Git Version
```bash
git --version
```
Displays the installed Git version, useful for troubleshooting and ensuring compatibility.

## Additional Tools

### Install Vim-Plug
```bash
curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
Downloads and installs the Vim-plug plugin manager for Vim.

```bash
wget -P ~/.vim/autoload https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
Alternative method to install Vim-plug using wget instead of curl.

### Delete Git Repository
```bash
rm -rf .git
```
Permanently removes the Git repository metadata without affecting the working files, effectively "ungitting" a directory.
