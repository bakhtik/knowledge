# Undoing things in Git

- [Amending last commit](#amending-last-commit)
- [Unstaging a staged file](#unstaging-a-staged-file)
- [Unmodifying a modified file](#unmodifying-a-modified-file)
- [Undoing things with git restore](#undoing-things-with-git-restore)
- [Unstaging a staged file in git restore](#unstaging-a-staged-file-in-git-restore)
- [Unmodifying a modified file with git restore](#unmodifying-a-modified-file-with-git-restore)


There are tools for undoing changes. Be careful, as you can't always undo some of these undos.

## Amending last commit

If you want to redo last commit, make the additional changes you forgot, stage them, and commit again using `--amend` option.

```console
$ git commit --amend
```

This command takes your staging area and uses it for the commit. You can use the technique without changes in staging are just to change message of the last commit.

This *replaces* old commit entirely with the new one as if it never happened.

Amending allows you to make minor improvements to the last commit, without clattering the repository history.

## Unstaging a staged file

Use `git reset HEAD <file>...` to unstage (before Git version 2.23.0)

```console
$ git status -s
M  development/git/undo.md
$ git reset HEAD development/git/undo.md
Unstaged changes after reset:
M	development/git/undo.md
$ git status -s
 M development/git/undo.md
```

The operation is relatively safe as the file in the working directory is not touched.

## Unmodifying a modified file

Use `git checkout -- <file>...` to discard changes in working directory.

**Warning!** It is a dangerous command. Any changes you made to that file are gone.

Anything that is *committed* can almost always be recovered.

## Undoing things with git restore

Git version 2.23.0 introduced a new command: `git restore` as an alternative to `get reset`.

## Unstaging a staged file in git restore

Use `git restore --staged <file>...` to unstage the file

## Unmodifying a modified file with git restore

Use `git restore <file>...` to discard changes in working directory.

**Warning!** It is a dangerous command. Any changes you made to that file are gone.
