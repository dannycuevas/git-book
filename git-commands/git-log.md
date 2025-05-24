
# GIT LOG
https://git-scm.com/docs/git-log

- It has many capabilities, like you can filter things out based on;
	- Who wrote the commits
	- When they were committed (dates of the commits)
	- Etc.

- Display only the very last commit
- You can also use it to display the last 2, or 3 commits, etc
```
git log -2
```

- Look at the history of commits in the current branch, to see from "what" branch it came from and when
```
git log --graph --decorate
```

### Commit Formatting "--pretty" option

"--pretty"
-It allows to pretty print or change the format of the logs (how they are printed out)

- This will be a more concise output, it will only display the comments for from each one of our commits
- It does not display any other information other than the commit message
```
git log --pretty="- %s"
```

- Create a text file, using the git log output (in this case, we are only filtering commit comments)
- Creating a text file out of this output can allow you to easily search through it if you are looking for something really specific

```
git log --pretty="- %s" > log-file-name.txt
git log --pretty="- %s" > gitlog-output.txt
```

### git log --oneline command

-Shorthand for "--pretty" and "--abbrev-commit" used together
-This is massive to help you READ ALL of the commits in the current repo
-Will also show each commits HASH
```
git log --oneline
```

### git log on another branch
```
git log BRANCH-NAME
```

- This will allow you to get the logs from any other branch, by name, from whatever branch you are on at that moment
