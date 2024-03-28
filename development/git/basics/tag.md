# Git Basics - Tagging

- [Listing your tags](#listing-your-tags)
- [Creating tags](#creating-tags)
- [Annotated tags](#annotated-tags)
- [Lightweight tags](#lightweight-tags)
- [Tagging later](#tagging-later)
- [Sharing tags](#sharing-tags)
- [Deleting tags](#deleting-tags)
- [Checking out tags](#checking-out-tags)

Git has the ability to tag specific point in a repository's history as being important. Typically, people use this functionality to mark release points (`v1.0`, `v2.0`, etc.).

## Listing your tags

Type `git tag` to list the existing tags.

You can also search for tags that match a particular patter:

```console
$ git tag -l "v1.8.5*"
v1.8.5
v1.8.5-rc0
v1.8.5-rc1
v1.8.5.1
```

## Creating tags

Git supports two types of tags:

- lightweight
- annotated

## Annotated tags

Annotated tags are stored as full objects, checksummed, can be signed and verified with GNU Privacy Guard (GPG), and contain:

- tagger name
- email
- date

```console
$ git tag -a v1.4 -m "my version 1.4"
$ git tag
v0.1
v1.3
v1.4
```

The `-m` specifies a tagging message.

You can see the tag data along with the commit that was tagged by using the `git show` command:

```console
$ git show v1.4
tag v1.4
Tagger: user <user@example.com>
Date:   Tue Mar 26 15:33:09 2024 -0700

my version 1.4

commit ca82a6...
Author: user <user@example.com>
Date:   Tue Mar 25 10:15:00 2024 -0700

   <commit message>
```

## Lightweight tags

They used if you want a temporary tag or for some reason don't want to keep the other information. This is basically the commit checksum stored in a file. To create a lightweight tag just provide a tag name:

```console
$ git tag v1.4-lw
$ git tag
v0.1
v1.3
v1.4
v1.4-lw
```

Run `git show` on the tag and you can see just the commit information.

```console
$ git show v1.4-lw
tag v1.4-lw
commit ca82a6...
Author: user <user@example.com>
Date:   Tue Mar 25 10:15:00 2024 -0700

   <commit message>
```

## Tagging later

You can also tag commits after you've moved past them.

To tag the commit, you specify the commit checksum (or part of it) at the end of the command.

```console
$ git tag -a v1.2 9fceb02
```

## Sharing tags

By default, the `git push` command doesn't transfer tags to remote servers. You will have to explicitly push tags - you can run `git push origin <tagname>`.

```console
$ git push origin v1.5
```

You can transfer all of your tags with `--tags` option.

```console
$ git push origin --tags
```

Now, when someone else clones or pull from your repository, they will get all your tags as well.

The `git push <remote> --follow-tags` will push only annotated tags.

## Deleting tags

To delete a tag on your local repository, you can use `git tag -d <tagname>`.

```console
$ git tag -d v1.4-lw
Deleted tag 'v1.4-lw` (was e7d5add)
```

To delete a tag from a remote server you can use:

- `git push <remote> :refs/tags/<tagname>`
- `git push <remote> --delete <tagname>`

## Checking out tags

If you want to view the versions of files a tag is pointing to, you can use a `git checkout` of that tag, although this puts your repository in "detached HEAD" state, which has some ill side effect.

```console
$ git checkout v2.0.0
Note: switching to 'v2.0.0'.

You are in 'detached HEAD' state...
```

In "detached HEAD" state, if you make any changes and then create a commit, the tag will stay the same, but you new commit won't belong to any branch and will be unreachable, except by the exact commit hash. Thus, if you need to make changes - say you're fixing a bug on an older version, for instance - you will generally want to create a branch:

```console
$ git checkout -b version2 v2.0.0
Switched to a new branch 'version2'
```

If you do this and make commit, your `version2` branch will be slightly different that your `v2.0.0` tag since it will move forward with your new changes, so do be careful.
