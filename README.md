## Learn Github in easy way

### Install Gitbash in Linux
##### [Learn Github](https://guides.github.com/activities/hello-world/)

#### [Github official site](https://git-scm.com/book/en/v2)

```
sudo apt install git 
```

### Configuration/ Gitbash setup

#### --local
        By default, git config will write to a local level if no configuration option is passed. 
        Local level configuration is applied to the context repository git config gets invoked in. 
        Local configuration values are stored in a file that can be found in the repo's .git directory: .git/config
#### --global
        Global level configuration is user-specific, meaning it is applied to an operating system user. 
        Global configuration values are stored in a file that is located in a user's home directory. 
        ~ /.gitconfig on unix systems and C:\Users\\.gitconfig on windows
#### --system
        System-level configuration is applied across an entire machine. 
        This covers all users on an operating system and all repos. 
        The system level configuration file lives in a gitconfig file off the system root path. 
        $(prefix)/etc/gitconfig on unix systems. 
        On windows this file can be found at C:\Documents and Settings\All Users\Application Data\Git\config on Windows XP, and in C:\ProgramData\Git\config on Windows Vista and newer.
        
        Thus the order of priority for configuration levels is: local, global, system. 
        This means when looking for a configuration value, Git will start at the local level and bubble up to the system level.

```
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

### Create new .git repository
    Compared to SVN, the git init command is an incredibly easy way to create new version-controlled projects. Git doesn’t require you to create a repository, import files, and check out a working copy. Additionally, Git does not require any pre-existing server or admin privileges. All you have to do is cd into your project subdirectory and run git init, and you'll have a fully functional Git repository. Transform the current directory into a Git repository. 
    This adds a .git subdirectory to the current directory and makes it possible to start recording revisions of the project. Create an empty Git repository in the specified directory. Running this command will create a new subdirectory called containing nothing but the .git subdirectory.
    If you've already run git init on a project directory and it contains a .git subdirectory, you can safely run git init again on the same project directory. It will not override an existing .git configuration.
```
git init
```
### Add project/new changes in staging area
    The `git add` command adds new or changed files in your working directory to the ***Git staging area***. 
    `git add` is an important command - without it, no git commit would ever do anything. Sometimes, `git add` can have a reputation for being an unnecessary step in development. But in reality, `git add` is an important and powerful tool. `git add` allows you to shape history without changing how you work.
```
git add .
```

```
git commit -m "Commit"
```

```
git remote add origin <Git repository URL>      //
```

```
git push -u origin master
```

// Clone existing project
6. git clone <branch-path>

// Once project clone in local then traverse to project folder
7. cd <project folder>

// To take latest changes
8. git pull

// If there are branches and want to get all data then fetch
9. git fetch --all

// Check how many branches are present in Git
10. git branch
11. git branch -a

// Create new branch
13. git checkout -b <branch-name> --no-track

// Navigate exiting branch
14.  git checkout <branch-name>

// Navigate parent branch
15. git checkout

 // from any branch to master
16. git checkout master

// Merge code of Branch-1 with Branch--2
16. git checkout Branch-1
17. git merge Branch-2

//Check status of code if any new updates is in code
18. git status
//Add changes and then commit code then push on specific branch
// Push changes in current branch: -
19.  git push origin <branch-name>
//Delete Branch 
20. git branch -d <branch-name>

//Delete commit msg
git commit --amend -m "New commit message"





### search (regex)
```
git grep "regex"
```

### list all branches
```
git branch -a
```

### list remote branches
```
git branch -r
```

### checkout a branch on remote
make sure you don't use `origin`
```
git fetch
git checkout branchName
```

### Create a new branch
first create a branch
```
git checkout -b <branchName>
```

Create a new branch from an existing branch
```
git checkout origin/branchName -b newBranchName
```

Then push your new branch to the repo
```
git push origin <branchName>
```

### Create a branch from a commit
AKA Recover a deleted branch
```
git checkout -b <branch> <sha>
```

### revert all changes in a branch. Removes staged and working directory changes.
```
git reset --hard
```

### Resets index to former commit; replace `56e05fced` with your commit code. You can use git log to get commit code
```
git reset 56e05fced
```

### revert a file to the most recent commit
```
git checkout HEAD -- /somePath/file.txt
```

### to discard changes in working directory
```
git checkout -- <file>
```

### Checkout a file from another branch
```
git checkout origin/branchName  -- fileName.txt
```

### undo the last commit. Blow it out of the water.
```
git reset --hard HEAD~1
```

### undo your last commit but leave the files from that commit staged. 
```
git reset --soft HEAD~1
```

### delete local (untracked) files
```
git clean -f
```

### If you want to also remove directories, run 
```
git clean -f -d
```

### clean a folder
```
git clean -fxd {dir_path}
```

### commit a folder/file without staging it.
```
git commit /folderToCommit -m 'commit msg'
```

### list all branches (remote & local/remote only)
```
git branch -a
git branch -r
```

### Find out all branches a commit is on
```
git branch --contains <commit>
```

### display log with Tree
```
git log --pretty=format:"%h - %cr (%an) %s" --graph
```

### Merge Master into your local branch
```
git fetch
git merge origin/master
```
a shortcut to this is. They are both the same 
```
git pull origin master
```
or, if it's a busy repo.
```
git pull --rebase <remote name> <branch name>
```

### list conflicts
```
git diff --name-only --diff-filter=U
grep -lr '<<<<<<<' .
```

### Diff a conflict
```
git mergetool -t opendiff
```

### pull a branch , merge if conflicted use remote.
```
git pull -s recursive -X theirs origin ra
```

### show log with merged files
```
git log -m -1 --name-only
```

### Show the changes between two branches.
```
git diff --name-status master..branchName > changelog.txt
```

### Recover a deleted branch

Get the SHA of the last commit on the branch.

```
git checkout -b newbranchname 56e05fced
```

## Stashes

### save a stash
```
git stash save "My changes."
```

### list your saved stashes
```
git stash list
```

### apply a stash (Where stash@{1} is the stash you want to apply.)
```
git stash apply stash@{1}
```

### delete a branch on origin
```
git push origin --delete <branchName>
```

### delete a branch locally
```
git branch -d <branchName>
```

### Get all commits from a branch. For a release log, changelog etc.
```
git cherry -v develop mybranch
```

### Revert a commit that is origin/remote

This reverts the commit with a new commit.

First get the commit sha.

```
git revert -m 1 <commit-hash> 
git commit -m "Reverting the last commit which messed the repo."
git push -u origin master
```

# Utilities

### Get the status on all repos in a folder
```
find . -maxdepth 1 -mindepth 1 -type d -exec sh -c '(echo {} && cd {} && git status -s && echo)' \;
```

Save the results to a file.
```
find . -maxdepth 1 -mindepth 1 -type d -exec sh -c '(echo {} && cd {} && git status -s && echo)' \; > gitreport.txt
```

### Delete all local branches that don't exist on `origin`


run `git fetch -p` this removes the remote references.

run `git branch -vv`

then run the following script

```
git fetch -p && for branch in `git branch -vv | grep ': gone]' | awk '{print $1}'`; do git branch -D $branch; done
```

keywords: prune
