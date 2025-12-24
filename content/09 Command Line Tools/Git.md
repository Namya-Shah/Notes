### Global config user name

```bash
git config --global user.name "FIRST_NAME LAST_NAME"
```

- We use this to let git know who is committing the code and changes.
### Global config email
```bash
git config --global user.email "MY_NAME@example.com
```
- It is not necessary to have email of your github, gitlab, etc. You can write any email you want
### Global config editor
```bash
git config --global core.editor "EDITOR NAME"
```
### Default branch name

```bash
git config --global init.defaultBranch main
```
### Checking your settings
```bash
git config --list
```
### Getting help
```bash
git help <verb> --help
```
### Initialising a git repository
```bash
git init
```
### Showing your remotes
```bash
git remote -v
```
### Adding remote repositories
```bash
git remote
```
### Fetching and pulling from your remotes
```bash
git fetch <remote>
```
### Renaming and Removing Remotes
```bash
git remote rename old_name new_name
```

```bash
git remote remove file_name
```
### Git Aliases
```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```

### Basic Merge Conflicts

```bash
git merge iss53
```

### Pushing to main branch

```bash
git push --set-upstream origin main
```

### Cloning an Existing Repository
```bash
git clone <link>
```
### Cloning an Existing Repository and naming the repository with custom name

```bash
git clone <link> "REPO NAME"
```

### Checking the status of your files
```bash
git status
```
### Ignoring files
```bash
cat .gitignore
```
### Committing your changes

```bash
git commit -m "MESSAGE"
```

### Removing files

```bash
git rm "FILE NAME"
```

### Moving files

```bash
git mv file_from file_to
```

### Undoing things

```bash
git commit --amend
```

### Unmodifying a Modified File with git restore

```bash
git restore --staged <file>

```

### List all local branches

```bash
git branch

```

### List remote and local branches

```bash
git branch -a

```

### Create a local branch and switch to it

```bash
git checkout -b branch_name

```

### Switch to an existing branch

```bash
git checkout branch_name

```

### Push branch to remote

```bash
git push origin branch_name

```

### Rename current branch

```bash
git branch -m new_name

```

### Delete a local branch

```bash
git branch -d branch_name

```

### Delete a remote branch

```bash
git push origin branch_name

```

### Show commit history in singleline

```bash
git log --oneline

```

### Show commit history for last N commits

```bash
git log -2

```

### Show commit history for last N commits with diff.

```bash
git log -p -2

```

### Show all local file changes in the working tree

```bash
git diff

```

### Show changes made to a file

```bash
git diff myfile

```

### Show who changed what & when in a file

```bash
git blame myfile

```

### Show remote branches and their mapping to local

```bash
git remote show origin

```

### Delete all untracked files

```bash
git clean -f

```

### Delete all untracked files and directories

```bash
git clean -df

```

### Undo local modifications to all files

```bash
git checkout -- .

```

### Unstage a file

```bash
git reset HEAD myfile

```

### Get remote tags

```bash
git pull --tags

```

### Switch to an existing tag

```bash
git checkout tag_name

```

### List all tags

```bash
git tag

```

### Create a new tag

```bash
git tag -a tag_name -m "tag message"

```

### Push all tags to remote repo

```bash
git push --tags

```

### Save changes to a stash

```bash
git stash save "stash name" && git stash

```

### List all stashes

```bash
git stash list

```

### Apply a stash and delete it from stash list

```bash
git stash pop

```