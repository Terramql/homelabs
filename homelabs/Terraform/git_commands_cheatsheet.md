# Common Git Commands Cheat Sheet

This cheat sheet provides a quick reference for the most commonly used Git commands with practical examples.

## Repository Setup

### Initialize a new repository
```bash
git init
```
Example:
```bash
mkdir my-project
cd my-project
git init
# Creates a new .git directory in my-project
```

### Clone an existing repository
```bash
git clone <repository-url>
```
Example:
```bash
git clone https://github.com/username/project.git
# Creates a local copy of the remote repository
```

## Basic Commands

### Check status
```bash
git status
```
Example:
```bash
git status
# Shows modified files, staged changes, and untracked files
```

### Add files to staging area
```bash
git add <file>
git add .
```
Example:
```bash
git add index.html
# Stages only index.html

git add .
# Stages all modified and new files
```

### Commit changes
```bash
git commit -m "<message>"
```
Example:
```bash
git commit -m "Fix navigation bar responsiveness"
# Creates a commit with the specified message
```

### View commit history
```bash
git log
git log --oneline
```
Example:
```bash
git log --oneline
# Shows a condensed history like:
# a1b2c3d Fix navigation bar responsiveness
# e4f5g6h Add contact form
# i7j8k9l Initial commit
```

## Working with Remotes

### Add a remote repository
```bash
git remote add <name> <url>
```
Example:
```bash
git remote add origin https://github.com/username/project.git
# Adds a remote named "origin" pointing to the GitHub repository
```

### View remote repositories
```bash
git remote -v
```
Example:
```bash
git remote -v
# origin  https://github.com/username/project.git (fetch)
# origin  https://github.com/username/project.git (push)
```

### Push changes to remote
```bash
git push <remote> <branch>
```
Example:
```bash
git push origin main
# Pushes commits from local main branch to origin's main branch
```

### Pull changes from remote
```bash
git pull <remote> <branch>
```
Example:
```bash
git pull origin main
# Fetches and merges changes from origin's main branch to local main branch
```

## Branching

### Create a new branch
```bash
git branch <branch-name>
git checkout -b <branch-name>
```
Example:
```bash
git checkout -b feature/login-page
# Creates and switches to a new branch named "feature/login-page"
```

### List branches
```bash
git branch
```
Example:
```bash
git branch
# * feature/login-page
#   main
#   develop
```

### Switch branches
```bash
git checkout <branch-name>
```
Example:
```bash
git checkout main
# Switches from current branch to main branch
```

### Merge branches
```bash
git merge <branch-name>
```
Example:
```bash
git checkout main
git merge feature/login-page
# Merges feature/login-page branch into main branch
```

### Delete a branch
```bash
git branch -d <branch-name>
```
Example:
```bash
git branch -d feature/login-page
# Deletes the feature/login-page branch after it's been merged
```

## Syncing Workflow Examples

### Daily workflow example
```bash
# Start the day by getting latest changes
git checkout main
git pull origin main

# Create a feature branch for today's work
git checkout -b feature/new-feature

# Make changes and commit them
# ... edit files ...
git add .
git commit -m "Implement new feature"

# Push your branch to GitHub
git push -u origin feature/new-feature

# Create a Pull Request on GitHub
# ... work continues, make more commits ...

# Stay in sync with main while working
git checkout main
git pull origin main
git checkout feature/new-feature
git merge main
# Resolve any conflicts if needed

# After PR is approved and merged on GitHub
git checkout main
git pull origin main
git branch -d feature/new-feature
```

### Updating a fork example
```bash
# Add the original repository as upstream
git remote add upstream https://github.com/original-owner/original-repo.git

# Get changes from upstream
git fetch upstream

# Update your fork's main branch
git checkout main
git merge upstream/main

# Push the updated main to your fork
git push origin main
```

## Undoing Changes

### Discard unstaged changes
```bash
git checkout -- <file>
```
Example:
```bash
git checkout -- src/app.js
# Discards changes to src/app.js, reverting to last commit
```

### Unstage files
```bash
git restore --staged <file>
```
Example:
```bash
git restore --staged src/app.js
# Removes src/app.js from staging area but keeps modifications
```

### Amend last commit
```bash
git commit --amend
```
Example:
```bash
git add forgotten-file.js
git commit --amend
# Adds forgotten-file.js to the previous commit
```

### Reset to a previous commit
```bash
git reset --soft HEAD~1
git reset --hard HEAD~1
```
Example:
```bash
git reset --soft HEAD~1
# Undoes last commit but keeps changes staged

git reset --hard HEAD~1
# Completely discards last commit and all changes
```

## Temporary Storage

### Stash changes
```bash
git stash
```
Example:
```bash
git stash
# Temporarily stores all modified tracked files
```

### Apply stashed changes
```bash
git stash pop
```
Example:
```bash
git stash pop
# Applies stashed changes and removes them from stash
```

## Viewing Changes

### View changes before committing
```bash
git diff
```
Example:
```bash
git diff
# Shows unstaged changes

git diff --staged
# Shows staged changes that will be committed
```

### View changes between commits
```bash
git diff <commit1> <commit2>
```
Example:
```bash
git diff HEAD~1 HEAD
# Shows changes between the last commit and the one before it
```

## Tagging

### Create a tag
```bash
git tag <tag-name>
```
Example:
```bash
git tag v1.0.0
# Creates a lightweight tag at the current commit

git tag -a v1.0.0 -m "Version 1.0.0 release"
# Creates an annotated tag with a message
```

### Push tags to remote
```bash
git push origin --tags
```
Example:
```bash
git push origin --tags
# Pushes all tags to the remote repository
```

## Troubleshooting

### Check remote branches
```bash
git remote show origin
```
Example:
```bash
git remote show origin
# Shows detailed information about the remote repository
```

### Clean untracked files
```bash
git clean -n
git clean -f
```
Example:
```bash
git clean -n
# Shows which files would be removed (dry run)

git clean -f
# Removes all untracked files
```

### Recover deleted commits (within reflog timeframe)
```bash
git reflog
git checkout <commit-hash>
```
Example:
```bash
git reflog
# Shows a log of all ref updates including resets
# 1a2b3c4 HEAD@{0}: reset: moving to HEAD~1
# 5d6e7f8 HEAD@{1}: commit: Feature that was reset

git checkout 5d6e7f8
git checkout -b recovered-branch
# Recovers the deleted commit to a new branch
```

## Configuration

### Set user information
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Create aliases
```bash
git config --global alias.<shortcut> <command>
```
Example:
```bash
git config --global alias.co checkout
git config --global alias.st status
git config --global alias.br branch
# Now you can use git co instead of git checkout, etc.
```

### Set default branch name
```bash
git config --global init.defaultBranch main
```

Remember that these commands are just the beginning. As you become more comfortable with Git, you'll discover more advanced features and workflows that can enhance your productivity.
