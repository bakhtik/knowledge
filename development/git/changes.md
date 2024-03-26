# Git Basics - Recording changes

Typically, you’ll want to start making changes and committing snapshots of those changes into your repository each time the project reaches a *state you want to record*.

- [Initializing Git repository](#initializing-git-repository)
- [Cloning an existing repository](#cloning-an-existing-repository)
- [Checking the status of the repository files](#checking-the-status-of-the-repository-files)
- [Short status](#short-status)
- [Tracking new files and staging modified files](#tracking-new-files-and-staging-modified-files)
- [Ignoring files](#ignoring-files)
- [Viewing Your Staged and Unstaged Changes](#viewing-your-staged-and-unstaged-changes)
- [Committing Your Changes](#committing-your-changes)
- [Skipping the Staging Area](#skipping-the-staging-area)
- [Removing files](#removing-files)
- [Moving files](#moving-files)
- [Discarding changed of all unstaged files in the current working directory](#discarding-changed-of-all-unstaged-files-in-the-current-working-directory)

## Initializing Git repository

```console
$ cd path_to_the_project_directory
$ git init
```

## Cloning an existing repository

```console
$ git clone https://github.com/account/repository
```

## Checking the status of the repository files

```console
$ git status
```

Files statuses:

- **tracked:** files is the last snapshot, or new staged files
  - **unmodified:** same version of the file is in the last snapshot
  - **modified:** changed version of the file, not staged
  - **staged:** new file or changed version of the tracked file that was staged
- **untracked:** rest files

## Short status

```console
$ git status -s (or --short)
 M README
MM Rakefile
A  lib/git.rb
M  lib/simplegit.rb
?? LICENSE.txt
```

Output legend:

- ??: untracked
- A: new staged files
- M: modified

LR form (left/right):

- L: status of the staging area (when "git add" command was applied to the file)
- R: status of the working tree (current state fo the file)

Examples:

```
 M - file modified, but not staged
MM - file modified, staged, then modified again
M  - file modified and staged
A  - new filed that has been staged
```

## Tracking new files and staging modified files
 
```console
$ git add <files> (or use *)
```

This will set the changes in the files to be committed available *at the very moment* of issuing the command. Any subsequent modifications will be ignored during the committing the changes.

## Ignoring files

You can tell Git to not automatically add or even show files being untracked, like logs or executables.
You can create a file listing patterns to match them named **.gitignore**.

```
# comments
*.a     ignore all files end with '.a', works recursively throughout the entire working tree
*~      ignore all files end with tilde '~'
!*def.a    do not ignore files end with 'def.a'
/*.a    ignore all files end with '.a' in the current directory, no recursion
folder/ specify directory
```

- `(*)` matches zero or more characters
- `[abc]` matches any character inside bracket
- `(?)` matches a single character
- `[0-9]` matches any character between the characters
- `a/**/z` matches nested directories (a/z, a/b/z, a/b/c/z, and so on)

Examples,

```
# ignore all .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in any directory named build
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf
```

Library of good .gitignore files are [here](https://github.com/github/gitignore).

## Viewing Your Staged and Unstaged Changes

```console
$ git diff
```

`git diff` shows you the exact lines added or removed. The command compares what is in your working directory with what is in your staging area. It shows you only changes that are still *unstaged*.

```console
$ git diff --staged
```

`git diff --staged` compares your staged changes to your last commit.

## Committing Your Changes

The commit records the snapshot you set up in your staging area. Anything you didn't staged is still sitting there modified.

```console
$ git commit
```

Command launches your editor of your choice.

```console
$ git commit -m "message"
```

Command allows type commit message inline.

## Skipping the Staging Area

Adding the `-a` option to the `git commit` command makes Git automatically stage every file that *is already tracked* before doing the commit, letting you skip the `git add` part.

```console
$ git commit -a -m "message"
```

## Removing files

The `git rm` command removes file from your tracked files and from the working directory as well.

```console
$ git rm filename
```

Modified of staged file can be deleted using `-f` option. This is a safety feature to prevent accidental removal of data.

```console
$ git rm -f staged_file
```

In order to remove file from staging area (stop tracking) but keep it in the working directory use `--cached` option.

```console
$ git rm --cached staged_file
```

## Moving files

If you want to rename the file, use a `mv` command.

```console
$ git mv file_from file_to
```

## Discarding changed of all unstaged files in the current working directory

```console
$ git restore .
```
