<b>remote:</b> "origin"<br>
<b>branch:</b> "main"<br>

<b>origin</b> is your clone's primary remote repository, usually your own fork or a repository you have direct write access to. <b>upstream</b> is used to designate the original repository from which you forked, allowing you to track changes and synchronize your fork with the source project.

`-m` amend (add to prev. commit), message `git commit -a -m "Commit message"` <br>
`-b` create branch `git checkout -b branch-name` <br>
`-u` for the first push to set the upstream reference `git push -u origin branch-name"` <br>
`-v` verbose - provides detailed information,  `git remote -v` <br>


### Setup
- Set the name that will be attached to your commits and tags:<br>
`git config --global user.name "Your Name"`

- Set the email that will be attached to your commits and tags:<br>
`git config --global user.email "your_email@example.com"`

### Infos

- Shows the status of changes as untracked, modified, or staged:<br>
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

- Used when you've initialized a new local Git repository and want to link it to a remote repository on a service like GitHub, GitLab, or Bitbucket. t's also used when you want to add a second remote to your repository. This could be the case when you've forked someone else's repository (origin) and you also want to keep your fork synchronized with the original repository (upstream). <br>
`git remote add remote-name https://github.com/username/repository.git
`

- Clone a repository from a remote source:<br>
`git clone <url>`

- Add several files to the staging area:<br>
`git add . `<br>
`git add *.txt`<br>
`git add file1.txt file2.txt file3.txt`<br>
`git add directory_name/*`<br>

- Commit staged changes and amend (joind) them to the most recend commit:<br>
`git commit -a -m "Initial commit"`

- Fetches and merges changes on the remote server to your working directory.<br>
`git pull <remote>`

- useful after initializing a Git repository with an initial commit and then trying to pull from a remote repository that also has its own initial commit, resulting in unrelated histories..<br>
`git pull origin main --allow-unrelated-histories`

-  Pushes all the modified local objects to the remote repository and advances its branches.<br>
`git push <remote> <branch>`

- Downloads commits, files, and refs from a remote repository into your local repo. It updates your remote-tracking branches (e.g., origin/main). This command fetches the new data from the remote repository but does not integrate any of this new data into your working files or local branches.:<br>
`git fetch <remote>`

-  Description: Temporarily stores all the modified tracked files.<br>
`git stash`

-  Reapply stashed changes.<br>
`git stash pop`

### Branching

- List your branches. A * will appear next to the currently active branch.:<br>
`git branch`

- s used to rename the current branch to main.:<br>
`git branch -M main`

- Switches branches:<br>
`git checkout <branch-name>`

- create , delete branch:<br>
`git branch <new-branch-name>` `git branch -d <branch-name>`

- Merge the specified branch's history into the current one.:<br>
`git merge <branch-name>`

- used within Git to integrate changes from the main branch into the current branch by reapplying commits on top of the main branch's current state.:<br>
`git rebase <branch-name>`

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

- After making sure you're on the correct branch and it has commits, retry the force push:<br>
`git push -u origin main --force`




