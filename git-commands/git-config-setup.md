
**`git-config` - Get and set repository or global options**

- Check if GIT is already installed
```
git --version
```

- First Time using GIT
```
https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup#_editor
```

> git config --global user.name "Jhon Doe"
> git config --global user.email "jhondoe@mail.com"

> git config --global core.editor EDITOR.name
> git config --global core.editor emacs

- Check "if" the Git username has been configured
```
git config user.name
git config user.email
```

- Editing and configuring the user and user email in a simple way
```
git config --global --edit
```

- Display all of your local config values
- This not only includes your local values, but it can also display your remote repo information
```
git config --list
```
