
- Suppose you just made a commit and then realized you forgot to include a file, or maybe you made a typo in the commit message.

- Rather than making a brand new separate commit, you can "redo" the previous commit (it only works with the last commit), by using the "amend" option:
```
git commit --amend
```

- Git add that file (to stage that file)
- Then use the commit "amend" option, to be able to redo the last commit
- This will allow the last commit to also "commit" the new files that were recently staged
