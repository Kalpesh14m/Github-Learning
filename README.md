# Learn Github in easy way

![](https://user-images.githubusercontent.com/25608527/97915332-55a32100-1d77-11eb-9afa-77a68f4d8bf5.png)

## ![Learn Github](https://guides.github.com/activities/hello-world/)
## ![Github official site](https://git-scm.com/book/en/v2)

---
## How Github Works:

![](https://user-images.githubusercontent.com/25608527/97918865-d87aaa80-1d7c-11eb-9da1-16b17b766e1a.jpg)

![](https://user-images.githubusercontent.com/25608527/97918875-d9abd780-1d7c-11eb-9f9f-c8502d74d7be.jpg)

![](https://user-images.githubusercontent.com/25608527/97918878-da446e00-1d7c-11eb-991a-7559f2c726a2.jpg)

---

### Install Gitbash in Linux

`sudo apt install git`

---

### Configuration/ Gitbash setup

#### --local

By default, git config will write to a local level if no configuration option is passed. Local level configuration is applied to the context repository git config gets invoked in. Local configuration values are stored in a file that can be found in the repo's .git directory: .git/config

#### --global

Global level configuration is user-specific, meaning it is applied to an operating system user. Global configuration values are stored in a file that is located in a user's home directory. ~ /.gitconfig on unix systems and C:\Users\\.gitconfig on windows

#### --system

System-level configuration is applied across an entire machine. This covers all users on an operating system and all repos. The system level configuration file lives in a gitconfig file off the system root path. $(prefix)/etc/gitconfig on unix systems. On windows this file can be found at C:\Documents and Settings\All Users\Application Data\Git\config on Windows XP, and in C:\ProgramData\Git\config on Windows Vista and newer.

Thus the order of priority for configuration levels is: local, global, system. 
This means when looking for a configuration value, Git will start at the local level and bubble up to the system level.

```
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
git config --global color.ui true

git config --list
```
---

### Create new .git repository

![](https://user-images.githubusercontent.com/25608527/97918882-db759b00-1d7c-11eb-9b81-58994eed6410.jpg)

Compared to SVN, the git init command is an incredibly easy way to create new version-controlled projects. Git doesn’t require you to create a repository, import files, and check out a working copy. Additionally, Git does not require any pre-existing server or admin privileges. All you have to do is cd into your project subdirectory and run git init, and you'll have a fully functional Git repository. Transform the current directory into a Git repository. 

This adds a .git subdirectory to the current directory and makes it possible to start recording revisions of the project. Create an empty Git repository in the specified directory. Running this command will create a new subdirectory called containing nothing but the .git subdirectory.
If you've already run git init on a project directory and it contains a .git subdirectory, you can safely run git init again on the same project directory. It will not override an existing .git configuration.

`git init`

![](https://user-images.githubusercontent.com/25608527/97916085-7e77e600-1d78-11eb-9113-0318ec40e222.png)

---

### Tracking Files with Git

You'll run the command "git status" quite often. It's the same as calling a bank administrator to check if your things arrived or if anything has been moved to a different vault.

`git status`

Now we can answer the question, "Why does Git need to track files?" Before we commit any files to a local repository, Git wants to know what those files are. Git only knows what to commit when it's tracking files.

If there are no files in the root directory yet, Git shows that there's **nothing to commit**. Our safe deposit box (repository) is empty. To do anything further, we need to populate the root folder with at least one file. We've added my-new-file.txt to the root directory. Now we can move on to the next step.

![](https://user-images.githubusercontent.com/25608527/97916083-7ddf4f80-1d78-11eb-8c82-c355e42f519a.png)

When you run "git status" once more **(assuming you've added a file to the project's root directory)**, you'll get a different output. **Note:** the ___"Untracked files"___ message with the file "my_new_file.txt". Git conveniently informs us that we've added a new file to the project. But that isn't enough for Git. As Git tells us, we need to track "my_new_file.txt". In other words, we need to add "my_new_file.txt" to the staging area.

![](https://user-images.githubusercontent.com/25608527/97916079-7cae2280-1d78-11eb-8bd5-456dfb041f8b.png)

---

### Add project/new changes in staging area

![](https://user-images.githubusercontent.com/25608527/97918887-db759b00-1d7c-11eb-82f0-bf3b76c3f0e8.jpg)

The `git add` command adds new or changed files in your working directory to the ***Git staging area***. `git add` is an important command - without it, no git commit would ever do anything. Sometimes, `git add` can have a reputation for being an unnecessary step in development. But in reality, `git add` is an important and powerful tool. `git add` allows you to shape history without changing how you work.

Let's say you want to move some of your valuable effects to a lock box, but you don't know yet what things you'll put there. For now, you just gather things into a basket. You can take things out of the basket if you decide that they aren't valuable enough to store in a lock box, and you can add things to the basket as you wish. With Git, this basket is the staging area. When you move files to the staging area in Git, you actually gather and prepare files for Git before committing them to the local repository.

**`git add <file-name>`**

`git add my_new_file.txt`

That's it; you've added a file to the staging area with the "add" command. Don't forget to pass a filename to this command so Git knows which file to track.

But what has this "add" command actually done? Let's view an updated status (we promised that you'll often run "git status", didn't we?):

![](https://user-images.githubusercontent.com/25608527/97917163-14f8d700-1d7a-11eb-8101-02ebf7a87224.png)

The status has changed! Git knows that there's a newly created file in your basket (the staging area), and is ready to commit the file.

What if you create or change several files? With a basket as your staging area, you have to put things into the basket one by one. Committing files to the repository individually isn't convenient. What Git can do is provide alternatives to the "git add <file-name>" command.

Let's assume you've added another three files to the root directory: my-file.ts, another-file.js, and new_file.rb. Now you want to add all of them to the staging area. Instead of adding these files separately, we can add them all together:

`git add my-file.ts another-file.js new_file.rb`

![](https://user-images.githubusercontent.com/25608527/97917157-13c7aa00-1d7a-11eb-9c07-9396712172eb.png)

All you need to do is type file names separated by spaces following the "add" command. When you run "git status" once more to see what has changed, Git will output a new message listing all the files you've added:

Adding several files to the staging area in one go is much more convenient! But hold on a second. What if the project grows enormously and you have to add more than three files? How can we add a dozen files (or dozens of files) in one go? Git accepts the challenge and offers the following solution:

`git add .`

![](https://user-images.githubusercontent.com/25608527/97917262-3bb70d80-1d7a-11eb-98e2-44cbe67633bf.png)

Instead of listing file names one by one, you can use a period – yes, a simple dot – to select all files under the current directory. Git will grab all new or changed files and shove them into the basket (the staging area) all at once. That's even more convenient, isn't it? But Git can do even better.

There's a problem with the "`git add .`" command. Since we're currently working in the root directory, "`git add .`" **will only add files located in the root directory. But the root directory may contain many other directories with files**. How can we add files from those other directories plus the files in the root directory to the staging area? Git offers the command below:

`git add --all`

The option "--all" tells Git: "Find all new and updated files everywhere throughout the project and add them to the staging area." Note that you can also use the option "-A" instead of "--all". Thanks to this simple option, "-A" or "--all", the workflow is greatly simplified.

**Remember** when we told you that you can take things out of your imaginary basket? Git can also take things out of its basket by removing files from the staging area. To remove files from the staging area, use the following command:

`git rm --cached my-file.ts`

![](https://user-images.githubusercontent.com/25608527/97917779-052dc280-1d7b-11eb-8224-800cd8f9e66e.png)

In our example, we specified the command **"rm"**, which stands for remove. The **"--cached"** option indicates files in the staging area. Finally, we pass a file that we want to unstage. Git will output the following message for us:

`rm my_file.ts`

Git is no longer tracking my-file.ts. In this simple way, you can untrack files if necessary. As an alternative to `"rm --cached <filename>"`, you can use the `"reset"` command:

`git reset another-file.js`

![](https://user-images.githubusercontent.com/25608527/97917775-0363ff00-1d7b-11eb-998c-c39faeac1a99.png)

**You can consider "reset" as the opposite of "add".**

- `git add .` stages new files and modifications, without deletions. The important point about git add . is that it looks at the working tree and adds all those paths to the staged changes if they are either changed or are new and not ignored, it does not stage any 'rm' actions.

- `git add -u` stages modifications and deletions, without new files. It looks at all the already tracked files and stages the changes to those files if they are different or if they have been removed. It does not add any new files, it only stages changes to already tracked files.

- `git add -A` stages all changes.  It is a handy shortcut for doing both of those.

### Git Version 1.x:

![](https://user-images.githubusercontent.com/25608527/97915159-ffce7900-1d76-11eb-9f93-ee714c1ef058.png)

### Git Version 2.x:

![](https://user-images.githubusercontent.com/25608527/97915156-fe9d4c00-1d76-11eb-8ae8-9890d50d51ce.png)

---
### Committing Changes to Git

![](https://user-images.githubusercontent.com/25608527/97918890-dca6c800-1d7c-11eb-9676-e51c97da77fa.jpg)

Let's start with a quick overview of committing to the Git repository. By now, you should have at least one file tracked by Git (we have three). As we mentioned, tracked files aren't located in the repository yet. We have to commit them: we need to carry our basket with stuff to the lock box. There are several useful Git commands to do (almost) the same: move (commit) files from the staging area (an imaginary basket) to the repository (a lock box).

There's nothing difficult about committing to a repository. Just run the following command:

`git commit -m "Add three files"`

To commit to a repository, use the **"commit"** command. Next, pass the "commit" command the **"-m"** option, which stands for "message". Lastly, type in your **commit message**. We wrote "Add three files" for our example, but it's **recommended that you write more meaningful messages** like "Add admin panel" or "Update admin panel". 

![](https://user-images.githubusercontent.com/25608527/97918894-dd3f5e80-1d7c-11eb-99d4-3bcf48ce17ba.jpg)

**Note that** we didn't use the past tense! _A commit message must tell what your commit does_ – adds or removes files, updates app features, and so on.

Once we've run "git commit -m 'Add three files'", we get the following output:

![](https://user-images.githubusercontent.com/25608527/97918150-a74daa80-1d7b-11eb-8a0b-59485fc1f2f4.png)

The `message` tells us that there have been three files added to the current branch, which in our example is the master or the main branch. The `"create mode 100644"` message tells us that these files are regular non-executable files. The `"0 insertions(+)" and "0 deletions(-)"` messages mean we haven't added any new code or removed any code from the files. We actually don't need this information; it only confirms that the commit was successful.

![](https://user-images.githubusercontent.com/25608527/97918898-ddd7f500-1d7c-11eb-85ea-dd6106941cc4.jpg)

![](https://user-images.githubusercontent.com/25608527/97918899-de708b80-1d7c-11eb-9aa4-fc55da9c0d13.jpg)

`git remote add origin <Git repository URL>`

`git push -u origin master`

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
