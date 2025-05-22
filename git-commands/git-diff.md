
# GIT DIFF

-The "git diff" command is all about showing changes in git
-It is purely an informative command, it does not apply any sort of changes at all
-Example, in any given repo, there are many situations where we might wanna know WHAT changed between the LAST commits and our working repo

Display the current unsaved changes on the current branch, this is recommended to run before actually adding changes and committing them (for example; to check what changes you have made if you forgot before you "add" your changes)

-Or what has changed between the staging area AND the working directory
-Or what has changed between 2 branches, or 2 different files over a certain number of commits

## git diff (with no options)
-Lists all the changes in our working directory that are not staged for the next commit
-So it compares the staging area and our current working directory

## **Example code syntax**

-The plus sign `+` with the green text represent the newly added text
-The lines with `-` and red text mean the old text that is now gone
-The symbols `---` represent the old version of the file
-While the `+++` represent the new version of the file
-And for the new text that was added/change, it will show some context "text" that resides before and after the newly added text (if there is any)
-The text `@@ -7,3 +7,4 @@` tells us it is the beginning of a chunk of text where there were changes to be visualized

```
mitrandir  ubuntu-rogx  ~/git-bootcamp  master ◔  git diff
diff --git a/characters.txt b/characters.txt
index 2faf6fc..72a181e 100644
--- a/characters.txt
+++ b/characters.txt
@@ -7,3 +7,4 @@ Extra characters
    -daniel
    -nicole
    -megumin
+-valkiria
```

### git diff HEAD
-This one will list all the changes in the working directory since the LAST commit
-It is pointing to the last commit of HEAD, meaning whatever HEAD is at that specific moment, which could be any given branch
-This is use to see the last changes to any SPECIFIC branch

### git diff --staged
git diff --cached
-Both of them will show us the staged changes, ONLY the changes that are staged (the files that have been "git added" )
-Meaning "Only show me the staged changes, so show me what will be included in my Commit if I run git commit right now"

### git diff HEAD file-name
```
git diff HEAD file-name1 file-name2
```

-We can view the changes within a specific FILE by providing a file-name
-Example
`git diff HEAD characters.txt`

### git diff comparing 2 branches
```
git diff branch1..branch2
```

-This will list the changes between the tips of branch1 and branch2
-It will include ALL the files in the branches, but you can narrow it down manually if needed

### git diff to compare 2 files
```
git diff commit1..commit2
```

-To compare 2 different commits, not necessarily HEAD so it can be any pair of commits even from the past
-Example
```
git log --oneline
git diff 42171df..cf877be
```
