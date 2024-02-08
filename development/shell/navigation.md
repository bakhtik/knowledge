# Navigation in shell

- [Understanding the Filesystem Tree](#understanding-the-filesystem-tree)
- [The current working directory](#the-current-working-directory)
- [Listing the content of a directory](#listing-the-content-of-a-directory)
- [Changing the current working directory](#changing-the-current-working-directory)
- [Some helpful shortcuts](#some-helpful-shortcuts)
- [Important facts about filenames](#important-facts-about-filenames)

You can navigate Linux filesystem using following commands:

- `pwd` - print name of current working directory
- `cd` - change directory
- `ls` - list directory contents

## Understanding the Filesystem Tree

Linux organizes its files in a *hierarchical directory structure* - a tree-like pattern of directories.

The *root directory* is the first directory in the filesystem.

Unix-like systems always have a single filesystem tree where storage devices are attached (*mounted*) at various points on the tree.

## The current working directory

You can imagine the filesystem as a maze shaped like an upside-down tree where you able to stand somewhere in the middle of it.

The *current working directory* is the directory you are standing at the moment.

Use the `pwd` command to display the current working directory:

```console
[user@host ~]$ pwd
/home/user
```

Each user account is given its own *home directory*, the only place user is allowed to write files. When user log in to system, his current working directory is set to his home directory.

## Listing the content of a directory

Use the `ls` command to list the files and directories in the current working directory.

```console
[user@host ~]$ ls
Desktop
Documents
Downloads
Music
Pictures
Public
Templates
Videos
```

## Changing the current working directory

Use the `cd` command to change your working directory: type `cd` followed by the pathname of the desired working directory.

A *pathname* is the route along the branches of the tree to the destination. Pathnames can be absolute or relative.

### Absolute pathnames

An *absolute pathname* begins with the root directory (represented by the leading slash in the pathname) and follows the tree to the directory or file.

`/usr/bin` - absolute pathname to the directory with most system programs installed.

The shell prompt is usually set up to automatically display the name of the working directory.

### Relative pathnames

A *relative pathname* starts from the working directory by using special symbols for relative positions.

- the `.` symbol refers to the working directory
- the `..` symbol refers to the working directory's parent directory

```console
[user@host bin] cd ..
[user@host usr] pwd 
/usr
[user@host usr] cd ./bin
[user@host bin] pwd 
/usr/bin
```

In almost all cases you can omit the `./` because it is implied.

Previous example can be rewritten as follows:

```console
[user@host usr] cd bin
```

## Some helpful shortcuts

| Shortcut | Result |
| -------- | ------ |
| `cd`     | Changes the working directory to you home directory |
| `cd -`   | Changes the working directory to the previous working directory |
| `cd ~username` | Changes the working directory to the home directory of *username*

## Important facts about filenames

- Filenames that begin with a period character are hidden. They can be listed using the `ls -a` command.
- Linux has no concept of a "file extension". The content and/pr purpose of a file is determined by other means.
- Limit he punctuation characters in the names of files to period, dash (hyphen), and underscore. *Most importantly, do not embed spaces in filenames*. If you want to represent spaces between words in a filename, use underscore character.
