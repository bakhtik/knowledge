# Git Branching - Branch Management

The `git branch` command with no arguments lists your current branches.

```console
$ git branch
  iss53
* master
  testing
```

The `*` character indicates the branch that you currently have checked out (i.e., the branch that `HEAD` points to). This means that if you commit at this point, the `master` branch will be moved forward with your new work.

To see the last commit on each branch, you can ran `git branch -v`.

To see which branches are already merged into the branch you're on, you can ran `git branch --merged`. Branches on this list without the `*` in front of them are generally fine to delete; you've already incorporated their work into another branch.

To see all the branches that contain work you haven't yet merged in, you can ran `git branch --no-merged`. You can add a branch name as an argument to ask about the merge state with respect to some other branch.

If you really do want to delete the branch and lose the work, you can force it with `-D`:

```console
$ git branch -D testing
```

## Changing a branch name

**Caution.** Do not rename branches that are still in use by other collaborators.

Rename the branch locally with the `get branch --move` command:

```console
$ git branch --move bad-branch-name corrected-branch-name
```

To let others wee the corrected branch on the remote, push it:

```console
$ git push --set-upstream origin corrected-branch-name
```

The `git branch --all` command lists all branches, including remote branches.

## Changing the master branch name

**Warning.** Changing the name of a branch like master/main/mainline/default will break the integrations, services, build scripts that your repository uses. Before you do this, consult with you collaborators.

Rename you local `master` branch into `main` with the following command:

```console
$ git branch --move master main
```

Push the branch to remote:

```console
$ git push --set-upstream origin main
```

The `main` branch is present on the remote. However, the old `master` branch is still present on the remote. Other collaborators will continue to use the `master` branch as the base of their work, until you make some further changes, like

- update any dependent projects
- update test configuration files
- adjust build/release scripts
- update repo settings
- update any references
- close/merge any pull requests that target the old branch

Now you can delete the `master` branch:

```
$ git push origin --delete master
```
