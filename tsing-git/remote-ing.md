
-By using Git Remote, we can tell our local repo about our cloud repo, like GitHub, so we can push our code to the cloud repo, to a "destination" that we call "remote"

-List and view your current remotes in a repository (-v is verbose, for more info)
If you have not added any remotes yet, then you will not see anything
```
git remote
git remote -v 
```


### Adding a new Remote
- A remote is really 2 things: a URL and a "label"
- To add a new remote we need to provide both values, with the .git URL

```
git remote add name url 
git remote add origin https://github.com/dannycuevas/git-notes.git
git push origin main
```

#### Origin?
- The term origin es just a conventional Git remote name, but it is not at all special, it is just a name for the URL
- You can name your remotes anything you want, but "origin" is just the standard, it is what you will see all the time
	- This is similar to "main" for branches

#### Example using ADO
- In the following example, I created a new branch at the remote repo level only (which is in Azure DevOps)
- Once it is there I did a `git pull` from my local to get the new branch from the remote and get it already set up in my local
- This is easier instead of manually setting up a remote origin
- Example picture below


#### Deleting Remote
- These are the commands to rename and delete remote repositories if needed
```
git remote rename OLDNAME NEWNAME
git remote remove NAME
```


### Remote already has files
- What happens when you add a remote to your local repo, but the remote already has one or more files?
- We will have to merge branches, and from there, we will be able to push our new commits to the remote

```
git remote add origin https://github.com/dannycuevas/git-notes.git
git remote -v
git pull     => This will give you the Git instructions on screen
git branch -M main
git branch
git pull origin main
git pull origin main --rebase
```

- The last command above, will allow you to merge your remote branch with your local branch into a single one, combining all files together, even if the branches are ahead o behind of each other
- Meaning, this command is tricky, use it with caution

- Use the following version if there are actually files to pull into your local when merging the remote and your local
```
git pull origin main --no-rebase
```


### Push / Different Branch
- When trying to push a different branch from your local repo to your remote, it will already have the "remote" set up (git remote -v)
- Now with the remote already set up, you need to do a push from the new branch once everything is committed 
```
git push origin BRANCH
git push origin main
git push origin superheroes
```


- This will work weather the branch already exists on GitHub or not
- If the branch does not yet exist, the Git will first create the branch for you, and then it will push your commits 

- We can also push a local branch with one name, into a remote branch with a different name, to do this we need to be specific about names in our command
```
git push origin LOCAL : REMOTE
git push origin localcats : remotedogs
```


### Push -u Option
- The u stands for Upstream
- The upstream of a local branch is like a connection pointing to a remote branch

- This will enable you to do things like simple
```
git push
```
