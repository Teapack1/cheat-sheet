<b>remote:</b> "origin"<br>
<b>branch:</b> "main"<br>

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

- Add several files to the staging area:<br>
`git add *.txt`<br>
`git add file1.txt file2.txt file3.txt`<br>
`git add directory_name/*`<br>

- Commit staged changes:<br>
`git commit -m "Initial commit"`

- After making sure you're on the correct branch and it has commits, retry the force push:<br>
`git push -u origin main --force`

### Info

- Shows the status of changes as untracked, modified, or staged:<br>
`git status`

- Displays the commit history for the current branch:<br>
`git log`

- Shows the file differences not yet staged:<br>
`git diff`

- List branhes:<br>
`git branch`

### Managing

- Switches branches:<br>
`git checkout <branch-name>`

- create , delete branch:<br>
`git branch <new-branch-name>` `git branch -d <branch-name>`

- merge branches:<br>
`git merge <branch-name>`

- Description: Fetches and merges changes on the remote server to your working directory.<br>
`git pull <remote>`

-Description: Pushes all the modified local objects to the remote repository and advances its branches.<br>
`git push <remote> <branch>`

-Description: Temporarily stores all the modified tracked files.<br>
`git stash`





