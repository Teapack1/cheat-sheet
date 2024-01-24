<b>remote:</b> "origin"<br>
<b>branch:</b> "main"<br>

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

- Shows the file differences not yet staged:<br>
`git diff`

-  Show the differences between the staged files and the latest version present:<br>
`git diff --staged`

### Repos basic
- Initialize a local Git repository:<br>
`git init`

- Clone a repository from a remote source:<br>
`git clone <url>`

- Add several files to the staging area:<br>
`git add *.txt`<br>
`git add file1.txt file2.txt file3.txt`<br>
`git add directory_name/*`<br>

- Commit staged changes:<br>
`git commit -m "Initial commit"`

### Branching

- List your branches. A * will appear next to the currently active branch.:<br>
`git branch`

- Switches branches:<br>
`git checkout <branch-name>`

- create , delete branch:<br>
`git branch <new-branch-name>` `git branch -d <branch-name>`

- Merge the specified branch's history into the current one.:<br>
`git merge <branch-name>`

### Repo Sync

- Fetches and merges changes on the remote server to your working directory.<br>
`git pull <remote>`

-  Pushes all the modified local objects to the remote repository and advances its branches.<br>
`git push <remote> <branch>`

- Fetch and merge any commits from the tracking remote branch.:<br>
`git fetch <remote>`

-  Description: Temporarily stores all the modified tracked files.<br>
`git stash`


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




