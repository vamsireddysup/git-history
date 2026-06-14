# Git Commands Documentation

A personal reference for Git workflows and commands. Covers everything from repository setup through GPG-signed commits.

## Table of Contents

- [Repository Setup](#repository-setup)
- [Basic Git Commands](#basic-git-commands)
- [Branching and Merging](#branching-and-merging)
- [Remote Repository Operations](#remote-repository-operations)
- [Configuration Commands](#configuration-commands)
- [GPG Signing](#gpg-signing)
- [Miscellaneous Commands](#miscellaneous-commands)
- [Additional Tools](#additional-tools)

---

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

---

## Basic Git Commands

### Check Repository Status

```bash
git status
```

Displays the state of the working directory and staging area, showing which changes have been staged and which files aren't being tracked.

### View Commit History

```bash
# Full log
git log

# Commits on remote not yet local (compact)
git log HEAD..origin/master --oneline
```

`git log` shows the chronological commit history with hashes, authors, dates, and messages.

### Add Files to Staging

```bash
# Stage all changes in current directory
git add .

# Stage a specific file
git add specific_file
```

### Commit Changes

```bash
# Standard commit
git commit -m "Commit message"

# GPG-signed commit
git commit -S -m "Message"
```

---

## Branching and Merging

### List Branches

```bash
# Local branches only
git branch

# All branches (local + remote-tracking)
git branch -a

# Remote-tracking branches only
git branch -r
```

### Create and Switch Branches

```bash
# Create from a remote branch and switch to it
git checkout -b branch_name origin/branch_name
```

### Delete a Branch

```bash
git branch -d branch_name
```

Deletes a branch after its changes have been merged. Prevents deletion of unmerged branches.

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

---

## Remote Repository Operations

### Add / Change Remote

```bash
# Add a new remote
git remote add origin git@github.com:username/repository-name.git

# Update an existing remote URL
git remote set-url origin git@github.com:username/repository-name.git
```

### View Remote Information

```bash
# List all remotes with URLs
git remote -v

# Detailed info on a specific remote
git remote show origin
```

### Push to Remote

```bash
# Push a branch
git push origin branch_name

# Push and set upstream tracking
git push -u origin branch_name

# Force push (use with caution — can overwrite remote history)
git push -f origin branch_name

# Delete a remote branch
git push origin --delete branch_name
```

### Pull from Remote

```bash
# Pull and merge
git pull origin branch_name

# Pull and rebase (replays local commits on top of remote)
git pull --rebase origin branch_name

# Pull with explicit merge commit
git pull --no-rebase origin branch_name

# Allow merging unrelated histories
git pull origin branch_name --allow-unrelated-histories
```

### Fetch from Remote

```bash
git fetch origin
```

Downloads objects and refs from the remote without merging, allowing inspection before integration.

---

## Configuration Commands

```bash
# Set GPG signing key globally
git config --global user.signingkey KEY_ID

# Enable colorized terminal output
git config --global color.ui auto

# Set default branch name for new repos
git config --global init.defaultBranch master
```

---

## GPG Signing

```bash
# Auto-sign all commits
git config --global commit.gpgsign true

# Auto-sign all tags
git config --global tag.gpgSign true

# Remove a previously set GPG format
git config --global --unset gpg.format
```

---

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

### Delete Git Repository Metadata

```bash
rm -rf .git
```

Permanently removes the `.git` directory without affecting working files — effectively "ungits" a directory.

---

## Additional Tools

### Install Vim-Plug

```bash
# Using curl
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
  https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

# Using wget
wget -P ~/.vim/autoload \
  https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

Downloads and installs the Vim-plug plugin manager for Vim.
