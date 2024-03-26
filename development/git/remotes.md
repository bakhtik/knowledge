# Git Basics - Working with Remotes

Remote repositories (remotes) are versions of your project that are hosted on the internet or network somewhere.

## Showing your remotes

Run the `git remote` command to see which remote servers you have configured:

```console
$ git remote
origin
```

`origin` is the default name Git gives to the server you cloned from.

You can specify `-v`, which shows you the URLs that Git has stored:

```console
$ git remote -v
origin	git@github.com:user/repository.git (fetch)
origin	git@github.com:user/repository.git (push)
```

## Adding remote repositories

The `git clone` command implicitly adds the `origin` remote. 

To add a new remote explicitly as a short name you can reference easily, run `git remote add <shortname> <url>`.

```console
$ git remote add u2 https://github.com/user2/repository2
$ git remote -v 
origin	git@github.com:user/repository.git (fetch)
origin	git@github.com:user/repository.git (push)
u2	git@github.com:user2/repository2.git (fetch)
u2	git@github.com:user2/repository2.git (push)
```

If you want to fetch all the information from u2 that you don't yet have in your repository, you can run `git fetch repo2`.

User2's `master` branch is now accessible locally as `u2/master` branch, and repository2 as `u2/repository2` branch.

## Fetching and pulling from your remotes

To get data from your remote projects, you can run:

```console
$ git fetch <remote>
```

The command goes out to that remote project and pulls down all the data from that remote project that you don't have yet.

If you clone a repository, the command automatically adds that remote repository under the name "origin".

Note that the `git fetch` command only downloads the data to your local repository - it doesn't automatically merge it with any of your work or modify what you're currently working on. You have to merge it manually.

If your current branch is set up to track a remote branch, you can use the `git pull` command to automatically fetch and then merge that remote branch into your current branch. The `git clone` command automatically sets up your local `master` branch to track the remote `master` branch.

## Pushing your remotes

When you have your project at a point you want to share, you have to push it upstream. The command for this is: `git push <remote> <branch>`. In example:

```console
$ git push origin master
```

## Inspecting a remote

If you want to see more information about a particular remote, you can use the `git remote show <remote>`.

It lists the URL for the remote repository as well as the tracking branch information.

## Renaming and removing remotes

You can run `git remote rename` to change a remote's shortname.

```console
$ git remote rename u2 wincent
$ git remote
origin
wincent
```

To remote a remote you can either use `git remote remove` or `git remote rm`:

```console
$ git remote remove wincent
$ git remote
origin
```
