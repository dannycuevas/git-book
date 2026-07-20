
### What is GIT?
-Git is a Version Control System, Free and Open Source
```
https://git-scm.com/docs
```

-What is a Version Control System?
It is a Software that helps track and manage changes to a set of files over time

-Version Control Systems offer:
Allow users to revisit earlier versions of files
Comparing changes made between different versions of the files
Undoing changes to the files
Sharing changes with other people
Or combine the changes
Git does this and more

# GIT WORK-PHASES

-Ignored Files
Files ignored by .gitignore file

-Working Area:
    -untracked
    -modified

-Staging Area:
    -changes ready to be committed with "commit -m" command
    -changes that are committed will be "staged"


# GIT CHEAT SHEET

-Check if GIT is already installed
git --version

> git config --global user.name "Daniel Momochi"
> git config --global user.email "danieldaniel@hotmail.com"

> git config --global core.editor EDITOR.name
> git config --global core.editor emacs

-Check "if" the Git username has been configured
```
git config user.name
git config user.email
```

-Editing and configuring the user and user email in a simple way
```
git config --global --edit
```

-List ALL of Git configuration settings
```
git config --global --list
```

𝗴𝗶𝘁 𝗶𝗻𝗶𝘁 : This is the very first command you'll need to use when starting a new project. It initializes a new Git repository in your current working directory. Or it can reinitialize an existing repo.

-GIT is going to monitor everything that happens in the main working directory including anything nested further down, like "child" or "grandchild" directories and so on.
-Before running GIT INIT, use GIT STATUS to verify that you are not already currently inside of a repo, because it might cause issues at some point. You can possibly fix these issues with deleting extra ".git" folders, just fyi.

𝗴𝗶𝘁 𝗰𝗹𝗼𝗻𝗲 <𝗿𝗲𝗽𝗼> : To work on an existing project, you'll want to clone (copy) it to your local machine. This command does that. From that URL repo, you will download the full history, all the commits, all the file, everything on your local machine.


# BRANCHING
-LINKS:
https://git-scm.com/docs/git-branch
https://git-scm.com/docs/git-switch

𝗴𝗶𝘁 𝗯𝗿𝗮𝗻𝗰𝗵 : This command will list all the current local branches in your current repository.

git branch -a : List all local and remote branches

𝗴𝗶𝘁 𝗯𝗿𝗮𝗻𝗰𝗵 <𝗯𝗿𝗮𝗻𝗰𝗵𝗻𝗮𝗺𝗲> : This command creates a new branch. Should not include spaces.

-This will create the new branch "based off of the HEAD" where we currently were, so it "points" to that same exact spot.
-Example last most recent commit
"commit 87efbe07466c60192d855e4a3151e9528f29253c (HEAD -> master, superheroes, SongsList)"

𝗴𝗶𝘁 𝗰𝗵𝗲𝗰𝗸𝗼𝘂𝘁 <𝗯𝗿𝗮𝗻𝗰𝗵𝗻𝗮𝗺𝗲> : If you want to switch to a different branch, old command version for some contexts.
https://git-scm.com/docs/git-checkout

-Always commit your changes before switching branches, or you will run into some conflicts.

git switch branch-name : Current and New command to switch to a different branch.
https://git-scm.com/docs/git-switch

git switch - : Return to the last branch

git switch -c branch-name : Create and switch to the newly created branch in a single command.

-Deletes a branch by their name:
git branch -d branch-name
git branch --delete branch-name

git branch -D : Shortcut for --delete --force, in other words, deleting a branch no matter its status.

git branch -v : Display all your branches with their Last commit only, in the form of a list, along with their commit message

git branch -r : List all remote branches in your local terminal
This is specially useful after cloning a remote repo into your local machine, so you can view all branches

-List branches by most recently committed to, from oldest to newest at the bottom, add color to the output, and show the commit subject line for each head
git branch -a --sort=committerdate --color -v 

### Branch Rename
-First change/switch to the branch that we want to rename
```
git branch -m new-name
git branch --move new-name

git branch -M new-name : shortcut for --move --force
```

### Merging Branches
https://git-scm.com/docs/git-merge
-We "merge" the "branches", we do not merge specific "commits"
-We always merge into the current HEAD of the current branch

-First switch into the branch you want to merge branches into (the receiving branch)
-Use "git merge" to merge the mentioned "target branch name" into the current branch we are sitting in
-VS Code will show you the changes that need to be manually approved, and will also give different option buttons to select from, so you can easily select what changes to apply when merging

𝗴𝗶𝘁 𝗺𝗲𝗿𝗴𝗲 <𝗯𝗿𝗮𝗻𝗰𝗵𝗻𝗮𝗺𝗲> : Once you've finished making changes in your current branch, run this command followed by the "target branch" to merge both branches

- **DevOps pro-tip for merging:** 
	- *1- Create a new "feature" branch* based of a working branch like "main" or "development", this way, if you work on another branch and play with it and if you mess something up, you still have your working branches left alone.
	- When you are "merging feature branches into main branches" you will not need to set up a "upstream/remote" target repository, you simply merge that feature branch into your main branch and the you push from main, eliminating the need to set up upstream again and again
	- 2- The other option, and maybe *the safest route, is "doing the merge twice over"*
		- but if you end up with a mess after merging, it will end up in your feature branch first only, and not on your main (to find out if there will be any conflicts first before doing any merging at all between the 2 branches);
		- Go to your main branch, pull any new changes "git pull" > switch branch to your feature branch and merge your main "git merge main" > now that feature and main are "in sync", now we merge the other direction > go back to your main "git switch main" and merge your feature "git merge feature"


# COMMIT / MAKE CHANGES

𝗴𝗶𝘁 𝘀𝘁𝗮𝘁𝘂𝘀 / git status -s
This command will show you any changes that are currently unstaged, along with the status of your git repo and its contents.
Git Status Docs:
https://git-scm.com/docs/git-status

𝗴𝗶𝘁 𝗮𝗱𝗱 <𝗳𝗶𝗹𝗲𝗻𝗮𝗺𝗲> : After you've made some changes to your files, you'll want to stage them for a commit. This command adds a specific file to the stage.

𝗴𝗶𝘁 𝗮𝗱𝗱 . 𝗼𝗿 𝗴𝗶𝘁 𝗮𝗱𝗱 -𝗔 : Instead of adding files one by one, you can add all your changed files to the stage with one command.

https://git-scm.com/docs/git-add

-NOTE:
-When ADDING, we can add changes to a group of files 1st and then commit those specific changes, and then make changes to a 2nd batch of different files and then commit the 2nd batch of files, these can help us "separate" changes made to different groups of files with different "commits".

𝗴𝗶𝘁 𝗰𝗼𝗺𝗺𝗶𝘁 -𝗺 "𝗖𝗼𝗺𝗺𝗶𝘁 𝗺𝗲𝘀𝘀𝗮𝗴𝗲" : Now that your changes are staged, you can commit them with a descriptive message.

-Display what was changed in the very last commit
git show

**git commit --amend :** Opens up the most recent commit and allows you to edit the commit message

**git diff** : Display the current unsaved changes on the current branch, this is recommended to run before actually adding changes and committing them (for example; to check what changes you have made if you forgot before you "add" your changes)


# UNDO COMMIT / CHANGES

**git reset --hard [commit-ID]** : By providing the commit-ID of a past commit, you can "hard reset" your branch (deleting Commits) all the way back - to that specific commit you want to go back to, thus the "hard reset" name.
(NOTE: do not forget, deletes all commits up to that commit you want to go back to).

| **Type**            | **Command**                      | **What It Does**                                                      |
| ------------------- | -------------------------------- | --------------------------------------------------------------------- |
| **Soft**            | `git reset --soft <commit-hash>` | Moves the pointer back, but **keeps changes staged**.                 |
| **Mixed** (default) | `git reset <commit-hash>`        | Moves the pointer back, **unstages changes** but keeps files.         |
| **Hard**            | `git reset --hard <commit-hash>` | ⚠️ Moves the pointer back, **deletes all changes** after that commit. |

This is how it would work:
(It **rewrites history** on the remote, which can mess up your teammates if they've pulled the bad commit)
```
# Step 1: Find the commit hash you want to go back to
git log --oneline

# Step 2: Hard reset the branch
git reset --hard <commit-hash>

# Step 3: Force push to overwrite remote history
git push origin main --force
```

**git revert** : Safest Way to Undo the latest Commit;
- It creates a new commit, and then it reverses the changes of the commit that was specified, in other words, a "new commit to reverse the changes of the latest commit".
- It preserves history and is safe for shared branches (safe for teams; it won’t break anyone else's clone)
- Meaning, it does not delete the latest commit, it will stay in history if your ever need to come back to it
```
# Step 1: Find the commit hash (use git log to view history)
git log --oneline

# Step 2: Revert the bad commit
git revert <target-commit>

# Step 3: Push the new "revert" commit to your remote
git push origin main
```

**git restore** : Roll Back File Changes Only. If you only want to revert changes to a single file or directory
`git restore index.html`

**git cherry-pick** : Bring Back a Specific Commit.
Lets you **pick a specific commit from one branch and apply it to another branch**, even if that commit doesn't belong to it. It’s like **copy-pasting** the commit to your current branch.
`git cherry-pick <commit-hash>`

>FINAL NOTE: "To roll back changes in Git, I can use:  
1️⃣ `git reset` to move the branch pointer back.  
2️⃣ `git revert` to safely undo a commit with a new reverse commit.  
3️⃣ `git restore` to undo file changes.  
4️⃣ `git stash` to temporarily save uncommitted work.  
5️⃣ `git cherry-pick` to recover specific commits.
We choose the method based on whether I want to rewrite history, revert safely, or temporarily stash work."


# REMOTE REPOSITORIES

𝗴𝗶𝘁 𝗿𝗲𝗺𝗼𝘁𝗲 -𝘃 : To check which remote servers are connected with your local repository, like checking what is the current repo hosted on the internet

**git remote get-url origin** : Display the actual URL of the remote repository that your local repo is connected to

𝗴𝗶𝘁 𝗽𝘂𝘀𝗵 <𝗼𝗿𝗶𝗴𝗶𝗻> <𝗯𝗿𝗮𝗻𝗰𝗵𝗻𝗮𝗺𝗲> : This command sends your commits to the remote repository.
-origin = remote repository name
-branchname = the name of the branch from that remote repo

**𝗴𝗶𝘁 𝗽𝘂𝘀𝗵 -u OriginRepo Branchname** : This command will be short for 
`-u is equal to --set-upstream`, and it sets up a new branch in the original remote repository, like one in GitHub or Azure DevOps
-branch-name, will also push a new branch to that new remote repo, example, like pushing a local branch to the remote repo on Azure DevOps and thus also creating that branch-connection between local and remote repo
-once this is set up, moving forward, from you already linked branch, you can just type "git push" as normal

-If the remote repo has change its name (or something like that), and you need to update the way the remote repo is being called in your local computer, use the following commands to list and update the naming
```
# list your remote repos configured for your local repo
git remote -v

# update the remote repo names
git remote rename [OLD-python-myprojects] [NEW-python-developer]
```

-And then update the URL manually for that repo as well
	-Why? GitHub is smart and keeps a "redirect", so things still work — but Git itself does not auto-update URLs when you rename your remote repo that is linked to your local repo
```
git remote set-url [NEW-python-developer] https://github.com/dannycuevas/NEW-python-developer.git
```

## Download Remote Changes

-As good practice, before you ever push something up to GitHub, you want to pull down and see if there are any changes
-If you want to check if the remote repository is ahead of your local repository, you can use the following Git command:

```
git fetch
git status -uno
git fetch origin main
```

-The git fetch command fetches the latest changes from the remote repository, but those changes will not be automatically integrated into our working local repo
-It lets you only see what others have been working on, without having to merge those changes into your local repo

-The `-uno` option with git status displays the status without showing changes that are not staged.
-After running these commands, you'll be able to see if the remote repository is ahead of your local repository and if there are changes you need to pull.

𝗴𝗶𝘁 𝗽𝘂𝗹𝗹 : If other people are also working on your project, you'll want to keep your local repo up-to-date with their changes. This command fetches and merges (integrates) any changes from the remote repository into your local repository

-Where we run the git pull command from, matters... Whatever branch we are on, that is where the changes being pulled will be merged

## Git Pull Merge Conflicts

- When you run git pull command, most of the times git can figure out how to merge things automatically, and some other times, there might be conflicts

- VS Code will show you the changes that need to be manually approved, and will also give different option buttons to select from, so you can easily select what changes to apply when merging
	- It will also show you, in the form of different colored text, the "Current Change" (the change made locally) and the "Incoming Change" (the change from GitHub)
	- **"Accept both changes"** - to do this, you can just click on the button that says "accept both changes", or, delete the extra text from the actual code so it looks like a single piece of code without any extra text
	- Then you save the file, then "add" the files to stating, and commit all these new changes
	- From here, you local will obviously ahead of the remote with these new merges and changes
	- So we will finally just "Push", and both local and remote will be up to date to the exact same point

## 𝗞𝗲𝘆 𝗗𝗶𝗳𝗳𝗲𝗿𝗲𝗻𝗰𝗲𝘀

𝗴𝗶𝘁 𝗳𝗲𝘁𝗰𝗵 𝘃𝘀 𝗴𝗶𝘁 𝗽𝘂𝗹𝗹: Both download data from a remote repository. However, git fetch just downloads it without integrating it, while git pull also merges it into your local files.

-So "git pull" is actually 2 commands in one, it is the combination of "git fetch" and "git merge".

𝗴𝗶𝘁 𝗺𝗲𝗿𝗴𝗲 𝘃𝘀 𝗴𝗶𝘁 𝗿𝗲𝗯𝗮𝘀𝗲: Both incorporate changes from one branch to another. git merge combines the source and target branches via a new commit, whereas git rebase moves or combines commits to a new base, making a cleaner history.

𝗴𝗶𝘁 𝗿𝗲𝘀𝗲𝘁 𝘃𝘀 𝗴𝗶𝘁 𝗿𝗲𝘃𝗲𝗿𝘁: Both are used to undo changes. git reset discards local changes completely, while git revert undoes public changes by creating a new reversing commit, thereby preserving history.


# GIT IGNORE

-Sometimes we want to "ignore" files in our current working directory, to prevent these files to be ever added to a "track" status, or "modified" or "committed" status, that way we can continuously modify those files and never having to fear committing them and pushing them by mistake, to do this, we tell GIT to "ignore" these files

-To ignore files, we sent them to our local ".gitignore" file
```
echo "FILE.NAME" >> .gitignore
echo "storyfinal.txt" >> .gitignore
```

>NOTE: As you might have noticed the .gitignore file itself may be listed as untracked. It is a good practice to track the .gitignore file with git

-To ignore directories use "/" at the end of their name

`.DS_Store` = will ignore files named `.DS_Store`
`folderName/` = will ignore an entire directory
`*.log` = will ignore any files with the `.log` extension
