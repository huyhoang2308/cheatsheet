# GIT
- Checkout and swith to it
```bash
git checkout -b my-new-branch
```

- Clone
```bash
git clone branch.git
```

-  branch
```bash
git branch [-a]
# List all local branches in repository. With -a: show all branches (with remote).
git branch [branch_name]
# Create new branch, referencing the current HEAD.
git checkout [-b][branch_name]
# Switch working directory to the specified branch. With -b: Git will create the specified branch if it does not exist.
git merge [from name]
# Join specified [from name] branch into your current branch (the one you are on currently).
git branch -d [name]
#  Remove selected branch, if it is already merged into any other. -D instead of -d forces deletion.
```

- Add file
```bash
# Add single file
git add file.txt

# Add multiple files
git add file1.txt file2.txt

# Add all text files in current dir
git add *.txt

# Add files in "my-dir"
git add my-dir`
```
- Config
```bash
git config --global --edit

#email
git config user.email

# Worktree
git config --worktree user.email

# Local (current repository)
git config --local user.email

# Global
git config --global user.email

# System
git config --system user.email

#Set up the default text editor
git config --global core.editor "'C:/path/to/executable' -parameters"

```

- Add file
```bash
# Edit the .gitignore file
# Ignore all txt files
*.txt

# Track "file1.txt" even if all other txt files are ignored
!file1.txt

# Ignore a file called "credentials" in the current directory
/credentials

# Ignore all files in any directory named "logs"
logs/

# ignore all txt files in the "logs" folder, but not "logs/apache/log.txt"
logs/*.txt

# ignore all ".txt" files in the "logs" directory and any of its subdirectories
logs/**/*.txt
```

- Log
```bash
# Show all commits
git log

# Show the most recent 5 commits
git log -5

# Show commits on one line
git log --oneline

# Show a patch with changes introduced by each commit
# Limiting the result to the most recent two commits
git log -p -2`

#Displaying commits made between 2021-01-01 (inclusive) and 2021-02-01 (exclusive):

# Using before and after
git log --after="2021-01-01" --before="2021-02-01"

# Using since and until
git log --since="2021-01-01" --until="2021-02-01"

# Filter the log entries by commit message containing a string
git log --grep="hello" -i
```

- Revert
```bash
git revert abc123
```

- Add remote repo
```bash
git remote add my-remote-name https://gitcheatsheet.org/example-git-repository.git
```

- Pull
```bash
# Pull from "origin" remote
git pull

# Pull from "my-remote-name" remote
git pull my-remote-name
```

- Push
```bash
# Push the current branch on the remote repository
git push

# Push the main (a.k.a. master) branch to the main branch on the "origin" remote
git push origin main
```
- Untrack files
```bash
#Untrack files AND remove them from working tree
git rm file1.txt file2.txt

#Untrack files from staging area, without removing them from the working tree
git rm --cached file1.txt file2.txt
```

- Reset
```bash
git reset HEAD fileToUnstage.txt

#Reset the working directory to the state of a specific commit
git reset --hard abc123
```

- Restorte
```bash
git restore --staged fileToUnstage.txt
```

- Rebase
```bash
# Regular rebase
git rebase other-branch

# Interactive rebase
git rebase -i other-branch
```

- Diff
```bash
#Show the changes of both staged and unstaged files since the last commit
git diff HEAD

#Show the changes of files that are staged
git diff --staged
```

- Cherry pick
```bash
git cherry-pick abc123
```

- Stash
```bash
# Stash local modifications
git stash push -m "My Stash Message"

# Include untracked files
git stash push -u -m "Including untracked files"

# Stash only specified files
git stash push -u -m "Stashing specific files" -- file1.txt file2.txt

# List the stash entries
git stash list

# Apply the LATEST stash entry (index 0)
git stash apply

# Apply SPECIFIC stash entry (index 1)
git stash apply stash@{1}

# Pop the LATEST stash entry (index 0)
git stash pop

# Pop a SPECIFIC stash entry (index 1)
git stash pop stash@{1}

# Drop the LATEST stash entry (index 0)
git stash drop

# Drop a SPECIFIC stash entry (index 1)
git stash drop stash@{1}

#Clear all the stash entries
git stash clear
```

- Tagging
```bash
git tag
# List all tags.
git tag [name] [commit sha]
#  Create a tag reference named name for current commit. Add commit sha to tag a specific commit instead of current one.
git tag -a [name] [commit sha]
# Create a tag object named name for current commit.
git tag -d [name]
# Remove a tag from local repository.
```