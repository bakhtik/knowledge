# Viewing the commit history

- [Viewing the history](#viewing-the-commit-history)
- [Viewing commits' difference](#viewing-commits-difference)
- [Viewing statistics](#viewing-statistics)
- [Changing the log output format](#changing-the-log-output-format)
- [Viewing branch and merge history as a graph](#viewing-branch-and-merge-history-as-a-graph)
- [Limiting log output](#limiting-log-output)

## Viewing the history

By default, `$ get log` command lists commits in reverse chronological order (most recent first):

- commit's SHA-1 checksum
- the author's name and email
- the date written
- the commit message

```console
$ get log
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    Change version number
```

## Viewing commits' difference

The `-p` or `--patch` option allows to show the difference introduced in each commit. This is helpful for the code review.

```console
$ git log -p -1
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    Change version number

diff --git a/Rakefile b/Rakefile
index a874b73..8f94139 100644
--- a/Rakefile
+++ b/Rakefile
```

## Viewing statistics

The `--stat` option provides some abbreviated statistics:

- a list of modified files
- how many files were changed
- how many lines in the files were added and removed

```console
$ git log --stat
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    Change version number

 Rakefile | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

## Changing the log output format

The `--pretty=<format>` option changes the log output to custom format.

The prebuilt formats are:

- `oneline`: each commit on a single line
- `short`, `full`, `fuller`

```console
$ git log --pretty=oneline
ca82a6dff817ec66f44342007202690a93763949 Change version number
085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7 Remove unnecessary test
```

The `--oneline` option is a shorthand for `--pretty=oneline --abbrev-commit`

The option value `format` allows you to specify custom format. This is useful for machine parsing.

```console
$ git log --pretty=format:"%h - %an, %ar : %s"
ca82a6d - Scott Chacon, 6 years ago : Change version number
085bb3b - Scott Chacon, 6 years ago : Remove unnecessary test
```

See useful specifiers [here](https://git-scm.com/book/en/v2/ch00/pretty_format).

## Viewing branch and merge history as a graph

The `--graph` option adds ACSII graph showing your branch and merge history.

## Limiting log output

The `-<n>` option, where n is an integer, allows to limit the number of log entries.

The `--since` and `--until` are the time-limiting options. They take a lot of formats.

```console
$ git log --since=2.weeks
$ git log --since="2008-10-01" --before="2008-11-01" 
```

The `--author` options allows you to filter on a specific author.

The `-S` option, Git's "pickaxe" option, shows only commits that changed provided string.

```console
$ git log -S funciton_name
```

You can limit commits that introduced in specific files.

```console
$ git log -- path/to/file
```

You can prevent to display of merge commits cluttering up the log history with the `log` option `--no-merges`

Options to limit the output of `git log` look [here](https://git-scm.com/book/en/v2/ch00/limit_options).

See this example,

```console
$ git log --pretty="%h - %s" --author='Junio C Hamano' --since="2008-10-01" \
   --before="2008-11-01" --no-merges -- t/
5610e3b - Fix testcase failure when extended attributes are in use
acd3b9e - Enhance hold_lock_file_for_{update,append}() API
f563754 - demonstrate breakage of detached checkout with symbolic link HEAD
d1a43f2 - reset --hard/read-tree --reset -u: remove unmerged new paths
51a94af - Fix "checkout --track -b newbranch" on detached HEAD
b0ad11e - pull: allow "git pull origin $something:$current_branch" into an unborn branch
```
