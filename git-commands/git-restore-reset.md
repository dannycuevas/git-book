
## Git Restore
-LINKS:
https://git-scm.com/docs/git-restore

- If you actually want to "restore" the file to its original state in the LAST commit
- You restore file by file manually using this command
```
git restore FILE-NAME
git restore variables.txt
```

- Restore a file back to the state it had in the specific commit
```
git restore -source=COMMIT FILE.NAME
```

- If you have accidentally "ADDED" a file to your "Staging Area" with git add, and you actually do not wish to include that file in the next commit, you can remove that file from staging
- Removing a file from the Staging Area (before committing a file), moves back the file in the previous state as a "modified file" only
```
git restore --staged FILE-NAME
git restore --staged story1.txt
```

- Example;
	- "un-staging" a file from the sagging area
	- then reverting that file back right to the previous state
```
git restore --staged bambi.txt
git restore bambi.txt
git status
```


## Git Reset
https://git-scm.com/docs/git-reset

- Reset command allows you to move "Staged" changes to "Unstaged" status
this is useful when you decided not to commit all the staged changes
```
git add .
git reset
```

- To undo your commits, you can use git reset to reset the repo back to a specific commit, also the commits will be gone as well
```
git reset COMMIT-HASH
git reset --hard COMMIT-HASH
```


## UNDO CHANGES

**git reset --hard [commit-hash]** : By providing the commit-hash of a past commit, you can "hard reset" your branch all the way back to that specific commit (NOTE: deletes new files that were created after that specific commit)

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


**git revert** : Safest Way to Undo a Commit, creates a new commit that reverses the changes of a specific commit. It preserves history and is safe for shared branches (safe for teams; it won’t break anyone else's clone)
```
# Step 1: Find the commit hash (use git log to view history)
git log --oneline

# Step 2: Revert the bad commit
git revert <commit-hash>

# Step 3: Push the new "revert" commit to remote
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
