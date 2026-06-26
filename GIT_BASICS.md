# Git Basics Guide

This guide covers the fundamental Git commands you need to know to manage version control for your projects.

## What is Git?

Git is a distributed version control system that tracks changes to files in your project. It allows you to:
- Save snapshots of your code at different points in time
- Collaborate with others on the same project
- Branch off to work on features independently
- Merge changes back together
- Revert to previous versions if needed

---

## Basic Git Commands

### 1. `git init`

**Purpose:** Initialize a new Git repository in your project directory.

**Usage:**
```bash
git init
```

**Example:**
```bash
$ mkdir my-project
$ cd my-project
$ git init
Initialized empty Git repository in /Users/user/my-project/.git/
```

This creates a hidden `.git` folder that contains all the version control metadata. You only need to run this once per project.

---

### 2. `git clone`

**Purpose:** Create a local copy of a remote repository on your computer.

**Usage:**
```bash
git clone <repository-url>
```

**Examples:**
```bash
# Clone a repository from GitHub
$ git clone https://github.com/ho3eines/NotBookLM.git

# Clone into a specific directory
$ git clone https://github.com/ho3eines/NotBookLM.git my-local-copy

# Clone using SSH (if you have SSH keys set up)
$ git clone git@github.com:ho3eines/NotBookLM.git
```

This is useful when you want to start working on an existing project. It downloads the entire repository history to your local machine.

---

### 3. `git status`

**Purpose:** Display the current state of your working directory and staging area.

**Usage:**
```bash
git status
```

**Example:**
```bash
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to stage for commit)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        new-feature.js
        config.json

nothing added to commit but untracked changes present (working directory dirty)
```

This command shows:
- Your current branch
- Modified files (tracked but not staged)
- Untracked files (new files Git doesn't know about yet)
- Files staged for commit

---

### 4. `git add`

**Purpose:** Stage files for the next commit. This tells Git which changes you want to include.

**Usage:**
```bash
# Stage a specific file
git add <filename>

# Stage all changes
git add .

# Stage all changes in a specific directory
git add <directory>/
```

**Examples:**
```bash
# Add a single file
$ git add README.md

# Add multiple files
$ git add file1.js file2.js file3.js

# Add all modified and new files in the current directory
$ git add .

# Add only modified files (not new files)
$ git add -u

# Interactively choose which changes to add
$ git add -p
```

**What happens when you stage files:**
- Files move from "untracked" or "modified" to the "staging area"
- The staging area holds the changes you want to commit
- Only staged changes will be included in your next commit

---

### 5. `git commit`

**Purpose:** Save staged changes to the repository with a descriptive message.

**Usage:**
```bash
git commit -m "Your commit message"
```

**Examples:**
```bash
# Create a commit with a message
$ git commit -m "Fix login bug in authentication module"

# Commit with a longer message
$ git commit -m "Update database schema

- Added user_preferences table
- Migrated existing user data
- Updated connection pooling settings"

# Stage and commit all tracked files in one step
$ git commit -am "Quick fix for typo in documentation"

# Amend the previous commit (add more changes or fix message)
$ git commit --amend -m "Corrected message"
```

**Best practices for commit messages:**
- Write clear, descriptive messages in the present tense
- Keep the first line under 50 characters
- Include details in the body (separated by a blank line)
- Reference issue numbers if applicable (e.g., "Fixes #42")

---

### 6. `git push`

**Purpose:** Upload your committed changes to a remote repository (like GitHub).

**Usage:**
```bash
git push <remote-name> <branch-name>
```

**Examples:**
```bash
# Push to the main branch on the origin remote
$ git push origin main

# Push to a feature branch
$ git push origin feature/new-login

# Push all branches
$ git push origin --all

# Push and set the upstream branch for future pushes
$ git push -u origin main
# After this, you can just use "git push" next time

# Force push (use with caution!)
$ git push origin main --force
```

**Common remotes:**
- `origin` - the default remote, usually your GitHub repository
- `upstream` - if you forked a project, this is the original repository

---

### 7. `git pull`

**Purpose:** Download changes from a remote repository and merge them into your current branch.

**Usage:**
```bash
git pull <remote-name> <branch-name>
```

**Examples:**
```bash
# Pull from the main branch on origin
$ git pull origin main

# Pull from your current tracking branch (simplest form)
$ git pull

# Pull and rebase instead of merge
$ git pull origin main --rebase

# Fetch updates without merging
$ git fetch origin
```

**What happens:**
1. Git downloads the latest changes from the remote
2. Git automatically merges them into your current branch
3. If there are conflicts, you'll need to resolve them manually

---

## Typical Git Workflow

Here's how these commands work together in a typical development workflow:

```bash
# 1. Clone a repository
$ git clone https://github.com/ho3eines/NotBookLM.git
$ cd NotBookLM

# 2. Check the status
$ git status

# 3. Make changes to files (using your editor)
# ... edit files ...

# 4. Check what changed
$ git status

# 5. Stage your changes
$ git add .

# 6. Commit your changes
$ git commit -m "Add new feature for user authentication"

# 7. Pull latest changes from remote (to avoid conflicts)
$ git pull origin main

# 8. Push your changes to remote
$ git push origin main
```

---

## Additional Useful Commands

### View commit history
```bash
git log
git log --oneline  # Concise view
git log --graph --oneline --all  # Visual branch structure
```

### Create and switch branches
```bash
git branch <branch-name>  # Create a branch
git checkout <branch-name>  # Switch to a branch
git checkout -b <branch-name>  # Create and switch in one command
```

### View differences
```bash
git diff  # Changes not staged
git diff --staged  # Changes staged for commit
git diff <branch1> <branch2>  # Compare branches
```

### Undo changes
```bash
git restore <filename>  # Discard changes in working directory
git restore --staged <filename>  # Unstage a file
git revert <commit-hash>  # Create a new commit that undoes changes
```

---

## Tips for Success

1. **Commit frequently** - Make small, logical commits that are easy to understand
2. **Write meaningful messages** - Future you will thank present you
3. **Pull before push** - Always sync with remote before pushing to avoid conflicts
4. **Use branches** - Create separate branches for features or bug fixes
5. **Review changes before committing** - Use `git diff` and `git status` often
6. **Don't commit sensitive data** - Never commit passwords, API keys, or personal information

---

## Getting Help

```bash
git help <command>  # Get detailed help for any command
git <command> -h    # Quick help for a command
```

Good luck with your Git journey!
