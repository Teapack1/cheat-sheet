<b>remote:</b> "origin"<br>
<b>branch:</b> "main"<br>

<b>origin</b> is your clone's primary remote repository, usually your own fork or a repository you have direct write access to. <b>upstream</b> is used to designate the original repository from which you forked, allowing you to track changes and synchronize your fork with the source project.

`-m` amend (add to prev. commit), message `git commit -a -m "Commit message"` <br>
`-b` branch `git checkout -b branch-name` <br>
`-u` for the first push to set the upstream reference `git push -u origin branch-name"` <br>
`-v` verbose - provides detailed information,  `git remote -v` <br>


### Setup
- Set the name that will be attached to your commits and tags:<br>
`git config --global user.name "Your Name"`

- Set the email that will be attached to your commits and tags:<br>
`git config --global user.email "your_email@example.com"`

### Infos

- Shows the status of changes as untracked, modified, or staged for next commit:<br>
`git status`

- Displays the commit history for the current branch:<br>
`git log`

- see the files that are currently being tracked by Git in your repository:<br>
`git ls-files`

- Shows the file differences not yet staged:<br>
`git diff`

-  Show the differences between the staged files and the latest version present:<br>
`git diff --staged`

-  List all remote repositories:<br>
`git remote -v`

### Repos
- Initialize a local Git repository:<br>
`git init`

- Connect repo to Github<br>
-> Go to Github and create "new repositary"

- Used when you've initialized a new local Git repository and want to link it to a remote repository on a service like GitHub, GitLab, or Bitbucket. t's also used when you want to add a second remote to your repository. This could be the case when you've forked someone else's repository (origin) and you also want to keep your fork synchronized with the original repository (upstream). <br>
`git remote add remote-name https://github.com/username/repository.git
`

- Unlink the current remote (typically named origin):<br>
`git remote remove origin`

- Change remote URL to a new one:<br>
`git remote set-url origin <new-url>`

- Add upstream repo:<br>
`git remote add upstream <original-repo-url>`

- Fetch all updates from upstream:<br>
`git fetch upstream`

- Merge the main branch from upstream:<br>
`git merge upstream/main`

- Clone a repository from a remote source:<br>
`git clone <url>`

- Clone particular branch:<br>
`git -b <branch> clone <url>`

- Get LFS files:<br>
`cd <repository-name>`<br>
`git lfs ls-files`<br>
`git lfs pull`<br>

- Add several files to the staging area:<br>
`git add . `<br>
`git add *.txt`<br>
`git add file1.txt file2.txt file3.txt`<br>
`git add directory_name/*`<br>

- remove the file from the staging area::<br>
`git reset HEAD path/to/your/file`

- Make your local files exactly match the remote repository's state, discarding any local changes.
`git reset --hard origin/<branch-name>`

- First, get a list of all your stashes:<br>
`git stash list`

- To see which files were changed in the most recent stash and a summary of the modifications:s:<br>
`git stash show -p"`

- Commit staged changes and amend (joind) them to the most recend commit:<br>
`git commit -a -m "Initial commit"`

- Fetches and merges changes on the remote server to your working directory.<br>
`git pull <remote>`

- useful after initializing a Git repository with an initial commit and then trying to pull from a remote repository that also has its own initial commit, resulting in unrelated histories..<br>
`git pull origin main --allow-unrelated-histories`

-  Pushes all the modified local objects to the remote repository and advances its branches.<br>
`git push <remote> <branch>`

-  Pushes and replaces everything present on the repo.<br>
`git push --force <remote> <branch>`

- Downloads commits, files, and refs from a remote repository into your local repo. It updates your remote-tracking branches (e.g., origin/main). This command fetches the new data from the remote repository but does not integrate any of this new data into your working files or local branches.:<br>
`git fetch <remote>`

  <b>`HEAD~1` refers to the commit before the latest commit, `HEAD~2` refers to two commits before the latest, and so on.</b>

-  If you just want to undo the commit but keep all changes from that commit staged (i.e., ready to be recommitted).<br>
`git reset --soft HEAD~1`

-  If you prefer to undo the last commit and also unstage the changes (returning them to your working directory).<br>
`git reset HEAD~1`

-  To completely undo the last commit and discard all changes made in that commit, run.<br>
`git reset --hard HEAD~1`

-  this will create a new commit that undoes the changes of the last commit.<br>
`git revert HEAD`

-  Description: Temporarily stores all the modified tracked files.<br>
`git stash`

-  Reapply stashed changes.<br>
`git stash pop`

### Branching

- List your branches. A * will appear next to the currently active branch.:<br>
`git branch`

- Rename the current branch to main.:<br>
`git branch -m main`

- Rename branch "master" to "main".:<br>
`git branch -m master main`

- Switches branches:<br>
`git checkout <branch-name>`

- create , delete branch:<br>
`git branch <new-branch-name>` `git branch -d <branch-name>`

- delete branch on remote (Github) :<br>
`git push origin --delete <branch-name>`

- Merge the specified branch's history into the current one.:<br>
`git merge <branch-name>`

- used within Git to integrate changes from the main branch into the current branch by reapplying commits on top of the main branch's current state.:<br>
`git rebase <branch-name>`

- Push all branches.:<br>
`git push origin --all`

- Listing all remote repos.:<br>
`git branch -r`

### Local project to existing repo

- Init:<br>
`git init`

- Link to GitHub repo:<br>
`git remote add origin <your-repo-url>`

- Check current barnch:<br>
`git branch`

- Switch to / create a branch:<br>
`git checkout -b main`

- Add all the files from local to staging area:<br>
`git add .`

- Commit staged changes:<br>
`git commit -m "Initial commit"`


## Rapid Prototyping / Vibe Coding Versioning

This guide outlines a straightforward process to save various states of your project, experiment freely, and merge the best results back into your main codebase.
<br>You need init git repo.

### Step 1: Create a Dedicated Branch for a Prototype (developement) Version

> To work on a specific prototype or feature variation without affecting the main codebase or other experiments, create a new branch. Think of a branch as a separate timeline or workspace for a specific set of changes. This keeps different development efforts distinct until a decision is made to combine them.

```bash
# Create a new branch and switch to it immediately
# Replace 'feature/prototype-name-v1' with a descriptive name:
# e.g., 'feature/landing-page-tabs-v1' or 'experiment/new-search-algorithm'
git checkout -b feature/prototype-name-v1
```

> `git checkout -b <branch-name>` is a shortcut that performs two actions: `git branch <branch-name>` (creates the branch) and `git checkout <branch-name>` (switches the working directory to that branch). Naming convention like `feature/...` or `experiment/...` helps organize branches.

### Step 2: Save the Current State (Commit Changes)

> Once a prototype reaches a state worth saving (even if it's just a starting point), its changes need to be recorded in the repository's history *on the current branch*. This involves telling Git which file changes to include (staging) and then saving them with a descriptive message (committing).

```bash
# Check which files have been modified, added, or deleted
git status

# Stage the changes you want to save in this version
# To stage all changes in the current directory:
git add . 
# Or stage specific files:
# git add path/to/file.py path/to/another/file.html

# Commit the staged changes to the branch's history
# Write a clear message describing what this version represents
git commit -m "feat: Implement initial prototype for [feature name]" 
# Example message: "feat: Initial tab layout for landing page v1"
# Using prefixes like 'feat:', 'fix:', 'experiment:' helps categorize commits.
```

> `git add` selects changes to be included in the next snapshot (commit). `git commit -m "message"` saves the staged changes permanently to the history of the currently active branch, associating them with the provided message.

### Step 3: Rapid Prototyping on Multiple Variants

> To try variations or improvements on an existing prototype without altering the saved version, create *new* branches *starting from* the branch you want to modify. This allows parallel development of different ideas based on a common starting point.

```bash
# First, ensure you are on the branch you want to base the experiment on
# For example, switch back to the first prototype branch:
# git checkout feature/prototype-name-v1 

# Create a new branch for the experiment, starting from the current branch
git checkout -b experiment/refine-prototype-feature-A

# --- Make code changes for Experiment A ---

# Save the changes for Experiment A on its own branch
git add .
git commit -m "experiment: Refine feature A layout"

# To start another experiment based on the *original* prototype:
# 1. Go back to the original prototype branch
git checkout feature/prototype-name-v1 
# 2. Create another new branch for the second experiment
git checkout -b experiment/redesign-prototype-feature-B

# --- Make code changes for Experiment B ---

# Save the changes for Experiment B on its branch
git add .
git commit -m "experiment: Redesign feature B interaction"
```

> Each `git checkout -b` creates a new, independent line of development starting from the code on the branch that was active when the command was run. Commits made on `experiment/refine-prototype-feature-A` do not affect `feature/prototype-name-v1` or `experiment/redesign-prototype-feature-B`.

### Step 4: Switching Between Saved Versions

> Easily navigate between different saved prototypes or experiments by switching branches. When switching, Git updates the files in the working directory to match the state of the last commit on the target branch.

```bash
# Switch to the first prototype branch
git checkout feature/prototype-name-v1

# Switch to the branch for Experiment A
git checkout experiment/refine-prototype-feature-A

# Switch to the branch for Experiment B
git checkout experiment/redesign-prototype-feature-B

# Check which branch is currently active
git branch 
# (The active branch will have an asterisk * next to it)
```

> `git checkout <branch-name>` updates the project files to the state recorded on `<branch-name>`. This allows quick comparison and testing of different versions.

### Step 5: Integrating the Chosen Version

> After experimenting, select the most successful prototype or version and merge its changes into the main development line (commonly the `main` or `develop` branch). Merging combines the history and changes from the selected feature branch into the target branch.

```bash
# Switch to the primary development branch (e.g., 'main')
git checkout main

# Merge the chosen feature branch into the current branch ('main')
# Replace 'experiment/refine-prototype-feature-A' with the name of the branch you want to keep
git merge experiment/refine-prototype-feature-A

# Git may open an editor to confirm the merge commit message, or create one automatically.
# If conflicts occur (changes in both branches affect the same lines), 
# Git will pause the merge and ask for manual resolution.

# After resolving any conflicts and staging the changes:
# git add . 
# git commit # Finalize the merge commit

# (Optional) Delete branches that are no longer needed after merging
# git branch -d experiment/refine-prototype-feature-A
# git branch -d experiment/redesign-prototype-feature-B 
# (Use -D to force delete if the branch wasn't merged)
```

> `git checkout main` ensures the receiving branch is active. `git merge <branch-to-merge>` integrates the changes from `<branch-to-merge>` into the currently active branch (`main`). This makes the chosen prototype part of the main project history. Deleting merged branches (`git branch -d`) helps keep the repository tidy.

# Git Workflow for Rapid Prototyping: Extended Guide

## Branch Management Fundamentals

### Listing and Navigating Branches

```bash
# List all local branches (current branch marked with *)
git branch

# List all branches including remote ones
git branch -a

# List branches with more details (last commit and message)
git branch -v

# List branches sorted by most recent commit
git branch --sort=-committerdate

# List branches that contain a specific commit
git branch --contains <commit-hash>
```

### Naming Conventions

- `main` - Main production-ready code
- `develop` - Current development version (unstable)
- `feature/name` - New feature development
- `experiment/feature-name-v1` - Experimental implementation
- `bugfix/issue-description` - Bug fixes
- `release/v1.0.0` - Release preparation
- `prototype/landing-page` - Working prototype

### Practical Development Strategy

1. **Feature-Based Workflow** (Recommended for most situations)
   - Start each feature from `main` or `develop`
   - Create multiple experiment branches from the feature branch
   - Merge the best experiment back to the feature branch
   - Merge the feature branch to `main`/`develop` when complete
   - Then start next feature from updated `main`/`develop`

2. **Parallel Features Workflow** (For independent features)
   - Multiple feature branches from `main`/`develop` simultaneously
   - Work on each independently
   - Merge each completed feature to `main`/`develop`

## Practical Commands for Prototyping

### Viewing Your Position and History

```bash
# Show current branch and status
git status

# Show commit history with branch visualization
git log --oneline --graph --decorate --all

# Show branches and their relationship
git show-branch --all
```

### Managing Experimental Branches

```bash
# Create experimental branch from current position
git checkout -b experiment/feature-xyz-v2

# Switch back to original feature branch
git checkout feature/xyz

# Delete branches after experiments are done
git branch -d experiment/feature-xyz-v1
```

### Merging Workflow

```bash
# After deciding on best implementation

# 1. First, switch to the target branch (where you want changes to go)
git checkout feature/xyz

# 2. Merge the winning experiment
git merge experiment/feature-xyz-v2

# 3. Later, when feature is complete, merge to main
git checkout main
git merge feature/xyz
```

## Best Practices

1. **Keep `main` stable** - Only merge complete, working features
2. **Create up to 2-3 experiment branches** per feature (avoid too many variants)
3. **Delete merged branches** to reduce clutter
4. **Commit frequently** within experiment branches
5. **Include descriptive prefixes** in commit messages: `feat:`, `fix:`, `refactor:`
6. **Merge completed features promptly** rather than waiting until project end
7. **Tag significant versions**: `git tag v0.1-prototype`

## Clone Repository with Specific Branches

```bash
# Clone with all branches
git clone <repo-url>

# Clone with only specific branch
git clone --branch <branch-name> --single-branch <repo-url>
```

Remember: The branch you're currently on serves as the context for all new commits. Creating a new branch doesn't automatically change any files - it just creates a new pointer to build upon.
