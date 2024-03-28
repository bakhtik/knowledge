# Git Basics - Get Aliases

If you don't want to type the entire text of the command, you can set up an alias for the command using `git config`.

```console
$ git config --global alias.co chechout
$ git config --global alias.br branch
$ git config --global alias.ci commit
$ git config --global alias.st status
``` 

So, instead of typing `git commit`, you just need to type `git ci`.

You can also create commands that you think should exist. For example, for unstaging a file:

```console
$ git config --global alias.unstage 'rest HEAD --'
```

This makes the following two commands equivalent:

```
$ git unstage fileA
$ git reset HEAD -- fileA
```

Or, you can add a `last` command to see the last commit:

```
$ git config --global alias.last 'log -1 HEAD'
```

You can run an external command by starting the command with a `!`:

```console
$ git config --global alias.visual '!gitk'
```
