---
{"dg-publish":true,"permalink":"/01_Reference/git reference/","title":"Comprehensive Git and GitHub Reference","tags":["devops","utility","linux"],"created":"2025-12-05T03:27:51.079+01:00"}
---


# Comprehensive Git and GitHub Reference

## Table of Contents

- [[#Git Basics]]
- [[#Configuring Git]]
- [[#Working with Repositories]]
- [[#Staging and Committing]]
- [[#Branching and Merging]]
- [[#Undoing Changes]]
- [[#Working with Remotes]]
- [[#Advanced Git]]
- [[#Git Workflows]]
- [[#GitHub Collaboration]]
- [[#Common Git Commands]]
- [[#Tips and Best Practices]]
- [[#Read More]]

---

## Git Basics

Git is a distributed version control system for tracking changes in source code during software development. It is designed for coordinating work among programmers, but it can be used to track changes in any set of files.

### Key Concepts

- **Repository (Repo):** A directory where your project's files and their history are stored.
- **Commit:** A snapshot of your repository at a specific point in time.
- **Branch:** A separate line of development. The default branch is `main` (or `master`).
- **Merge:** The process of combining changes from different branches.
- **Remote:** A version of your repository hosted on a server, like GitHub.
- **Clone:** A local copy of a remote repository.
- **HEAD:** A reference to the last commit in the currently checked-out branch.
- **Working Directory:** The files and folders you are currently working on.
- **Staging Area (Index):** A file that stores information about what will go into your next commit.

---

## Configuring Git

Proper configuration is essential for using Git effectively.

```bash
# Set your global username and email
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# Check your current configuration
git config --list

# Set your default editor
git config --global core.editor "vim"

# Set the default branch name
git config --global init.defaultBranch main

# Enable colorful output
git config --global color.ui auto
```

---

## Working with Repositories

```bash
# Initialize a new Git repository
git init

# Clone an existing repository from a URL
git clone <repository-url>

# Check the status of your repository
git status

# Show a more compact status
git status -s

# Display all ignored files
git status --ignored
```

---

## Staging and Committing

Prepare and save your changes to the repository's history.

```bash
# Stage a specific file for the next commit
git add <filename>

# Stage all changes in the current directory
git add .

# Interactively stage parts of a file
git add -p

# Commit the staged changes with a message
git commit -m "Your descriptive commit message"

# Stage all tracked files and commit in one step
git commit -a -m "Your message"

# Amend the last commit (change message or add files)
git commit --amend

# Remove a file from the staging area but keep it in the working directory
git rm --cached <filename>

# Preview files that would be removed
git rm -r -n <directory>

# Stop tracking a file that was previously committed
git rm --cached <filename>
```

---

## Branching and Merging

Manage parallel lines of development and integrate them.

```bash
# List all local branches
git branch

# List all remote branches
git branch -r

# List all local and remote branches
git branch -a

# Create a new branch
git branch <branch-name>

# Delete a branch (use -D to force delete)
git branch -d <branch-name>

# Switch to a different branch
git checkout <branch-name>

# Create a new branch and switch to it
git checkout -b <branch-name>

# Merge a branch into your current branch
git merge <branch-name>

# Abort a merge in case of conflicts
git merge --abort

# Resolve merge conflicts manually, then:
git add <conflicted-file>
git commit
```

---

## Undoing Changes

Correct mistakes and revert unwanted changes.

```bash
# Unstage a file
git reset <file>

# Revert changes to a file in the working directory
git checkout -- <file>

# Create a new commit that undoes the changes from a specific commit
git revert <commit-hash>

# Reset to a previous commit, discarding all changes since
git reset --hard <commit-hash>

# Reset to a previous commit, keeping changes unstaged
git reset --soft HEAD~1

# Restore a file to a specific commit's version
git restore --source=<commit-hash> <file>
```

---

## Working with Remotes

Collaborate with others by sharing your changes.

```bash
# Add a new remote repository
git remote add <remote-name> <url>

# List all remotes
git remote -v

# Fetch changes from a remote
git fetch <remote-name>

# Pull changes from a remote branch and merge them
git pull <remote-name> <branch-name>

# Push your changes to a remote branch
git push <remote-name> <branch-name>

# Force push (use with caution!)
git push <remote-name> <branch-name> --force

# Set an upstream branch for your local branch
git push -u <remote-name> <branch-name>
```

---

## Advanced Git

### Rebasing

Rebasing is an alternative to merging for integrating changes from one branch to another. It rewrites the commit history to create a linear sequence of commits.

```bash
# Rebase the current branch onto another branch
git rebase <base-branch>

# Start an interactive rebase to edit, squash, or reorder commits
git rebase -i HEAD~<number-of-commits>

# Continue a rebase after resolving conflicts
git rebase --continue

# Abort a rebase
git rebase --abort
```

### Cherry-Picking

Apply a specific commit from one branch to another.

```bash
# Apply a single commit to the current branch
git cherry-pick <commit-hash>
```

### Stashing

Temporarily save changes that are not ready to be committed.

```bash
# Stash your current changes
git stash

# List all stashed changes
git stash list

# Apply the most recent stash and remove it from the list
git stash pop

# Apply a specific stash
git stash apply stash@{2}

# Clear all stashes
git stash clear
```

---

## Git Workflows

Different strategies for managing branches and collaboration.

- **GitFlow:** A robust framework using feature branches, develop, release, hotfix, and main branches. Good for projects with scheduled releases.
- **GitHub Flow:** A simpler model where `main` is always deployable. Feature branches are created from `main` and merged back via pull requests.
- **Trunk-Based Development:** All developers work on a single branch (`trunk` or `main`), committing small, frequent changes.

---

## GitHub Collaboration

Leveraging GitHub for team-based development.

- **Forking:** Create a personal copy of a repository on GitHub.
- **Pull Request (PR):** Propose changes from your fork or a branch to be merged into the main repository.
- **Code Reviews:** Discuss and review changes within a pull request before merging.
- **Issues:** Track bugs, feature requests, and other tasks.

```bash
# Fork a repository (done on the GitHub UI)

# Clone your fork
git clone <your-fork-url>

# Add the original repository as an upstream remote
git remote add upstream <original-repo-url>

# Fetch changes from the upstream repository
git fetch upstream

# Merge changes from upstream/main into your local main
git merge upstream/main

# Keep your fork's main branch up-to-date
git pull upstream main
```

---

## Common Git Commands

| Command                     | Description                                      |
| --------------------------- | ------------------------------------------------ |
| `git log`                   | Show commit history                              |
| `git log --oneline --graph` | Show a condensed, graphical log                  |
| `git diff`                  | Show changes between commits, branches, or files |
| `git diff --staged`         | Show changes that are staged for the next commit |
| `git tag`                   | Create, list, or delete tags for specific commits|
| `git blame <file>`          | Show who last modified each line of a file       |
| `git show <commit-hash>`    | Show details of a specific commit                |
| `git reflog`                | View a log of all changes to branches and HEAD   |

---

## Tips and Best Practices

- **Write Clear Commit Messages:** Follow a convention (e.g., start with a verb, keep the subject line short).
- **Commit Early and Often:** Make small, logical commits.
- **Use `.gitignore`:** Keep your repository clean by ignoring generated files, logs, and dependencies.
- **Branch for Everything:** Create a new branch for every new feature, bug fix, or experiment.
- **Pull Before You Push:** Always sync with the remote before pushing your changes to avoid conflicts.
- **Squash Commits:** Clean up your history before merging a feature branch.

## Read More

- [[00_Fleeting_inbox/git workflows\|git workflows]] - Personal note
- [git-scm.com/documentation](https://git-scm.com/doc) - Official Git documentation
- [git-scm.com/book](https://git-scm.com/book/en/v2) - Pro Git e-book
- [atlassian.com](https://www.atlassian.com/git) - Atlassian Git tutorial
- [learngitbranching.js.org](https://learngitbranching.js.org/) - Learn Git branching
- [GitHub Skills](https://skills.github.com/)
- [youtube.com/video](https://www.youtube.com/watch?v=S7XpTAnSDL4) - "Git & Github tutorial | Visualised git course for beginner & professional developers in 2024" by JavaScript Mastery
- [youtube.com/video](https://www.youtube.com/watch?v=8JJ101D3knE) - "Git tutorial for beginners: Learn git in 1 hour" by Programming with Mosh
