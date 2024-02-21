# Exploring the System - Linux Shell

## More fun with ls

With `ls` command we can see directory contents and determine a variety of important file and directory attributes.

We can specify one or multiple directories to list:

```console
[user@host ~] ls ~ /usr

/home/user:
Desktop
Documents
Downloads
Music
Pictures
Public
Templates
Videos

/usr:
bin
games
lib
lib64
libexec
libx32
local
sbin
share
src
```

We can also change the format of the output to reveal more detail:

```console
[user@host ~] ls -l

total 308
rwxr-xr-x  2 user user  4096 Jul 31  2022 Desktop
drwxr-xr-x 17 user user  4096 Jan 11 11:49 Documents
drwxr-xr-x 49 user user 90112 Feb 16 13:59 Downloads
drwxr-xr-x  2 user user  4096 Oct  1 15:40 Music
drwxr-xr-x  4 user user 40960 Jan 18 15:05 Pictures
drwxr-xr-x  2 user user  4096 Apr 24  2020 Public
drwxr-xr-x  2 user user  4096 Apr 24  2020 Templates
drwxr-xr-x  8 user user  4096 Oct  2 15:46 Videos
```

By adding -l to the command, we changed the output to the long format.

## Options and arguments

Commands are often followed by one or more *options* that modify their behavior and, further, by one or more *arguments*, the items upon which the commands acts. So, most commands look something like this:

```console
command -options arguments
```

Options can be

- a single character precede by a dash, `ls -l`
- a *long options*, consisting of a word preceded by two dashes, `ls --reverse`
- multiple short options to be strung together, `ls -lt`

### Common ls options

| Option| Long Option 		| Description 			|
| ----- | --------------------- | ----------------------------- |
| -a	| --all			| List all files, including hidden (that begin with period) |
| -d	| --directory		| Use this option in conjunction with the -l option to see details about the directory rather that its content |
| -F	| --classify		| This option will append an indicator character to the end of each listed name (i.e., '/' to the directory |
| -h	| --human-readable	| Display sizes in human-readable format rather than in bytes |
| -l	|			| Display results in long format |
| -r	| --reverse		| Display results in reverse order. Ascending alphabetical order is a default order |
| -S	|			| Sort results by file sizes |
| -t	|			| Sort by modification time |

## A longer look at long format

### ls long listing fields

| Field		| Meaning |
| ------------- | ------- |
| `-rw-r-r--`	| Access rights to the file. First character - file type (`-` for regular file, `d` - directory). The next three characters are access rights for the file's owner, the next three - for members of the file's group, and the final three are for everyone else. |
| 1		| File's number of hard links. |
| root		| The user name of the file's owner. |
| root		| The name of the group that owns the file |
| 32059		| Size of the file in bytes. |
| 2012-04-03 11:05 | Date and time of the file's last modification |
| file.md	| Name of the file |

## Determining a file's type with `file`

Filenames in Linux are not required to reflect a file's contents.

Use the `file` command to determine the file's type.

```console
$ file filename
```

When invoked, the `file` command will print a brief description of the file's content.

## Viewing file contents with less

The `less` command is a program to view text files.

### What is "Text"?

Computers understands only numbers, and all data is converted to numeric representation.

One of the earliest representation systems is called ASCII text ("As-Key", American Standard Code for Information Interchange).

Text is a simple one-to-one mapping of characters to numbers.

Plain ASCII text files contain only the characters themselves and a few rudimentary control codes like tabs, carriage returns, and linefeeds.

### Less is More

The `less` command is user like this:

```console
$ less fielname
```

Once started, the `less` program allows you to scroll forward and backward through a text file.

The `less` program is an improvement of an earlier Unix program called `more`, that could scroll pages forward only.

`less` falls into the class of programs called *pagers*, programs that allow view text files in a page-by-page manner.

### less commands

| Command | Action |
|---------|--------|
| `page up` or b | Scroll back one page |
| `page down` or `Spacebar` | Scroll forward one page |
| `up arrow` | Scroll up one line |
| `down arrow` | Scroll down one line |
| G | Move to the end of the text file |
| 1G or g | Move to the beginning of the text file |
| /*characters* | Search forward to the next occurrence of the *characters* |
| n | Search for the next occurrence of the previous search |
| p | Search for the previous occurrence of the previous search |
| h | Display help screen |
| q | Quit `less` |

## A guided tour

The filesystem layout of the Linux system is specified in the [*Linux Filesystem Hierarchy Standard*](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html).

Many of the interesting files in Linux are in plain, human-readable text.

Regular users are largely prohibited from messing things up.

### Directories found on Linux

| Directory | Comments |
|-----------|----------|
| */* | The root directory, where everything begins |
| */bin* | Contains binaries (programs) that must be present for the system to boot and run |
| */boot* | Contains the Linux kernel, initial RAM disk image (for drivers needed at boot time), and the boot loader. <br><br> Interesting files:<br> - */boot/grub/grub.conf* or *menu.lst*, which are used to configure the boot loader<br> - */boot/vmlinuz*, the Linux kernel
