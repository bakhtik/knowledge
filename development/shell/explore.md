# Exploring the System - Linux Shell

- [More fun with ls](#more-fun-with-ls)
- [Options and arguments](#options-and-arguments)
- [A longer look at long format](#a-longer-look-at-long-format)
- [Determining a file's type with `file`](#determining-a-files-type-with-file)
- [Viewing file contents with less](#viewing-file-contents-with-less)
- [A guided tour](#a-guided-tour)
- [Symbolic Links](#symbolic-links)

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
| */dev* | Contains *device nodes*. "Everything is a file" also applies to devices. Here is where the kernel maintains a list of all the devices it understands. |
| */etc* | Contains all of the system-wide configuration files. It also contains a set of shell scripts that start each of the system services at boot time.<br><br> Interesting files:<br> - */etc/crontab/*, a file that denotes when automated jobs will run<br> - */etc/fstab*, a table of storage devices and their associated mount points<br> - */etc/passwd*, a list of the user accounts |
| */home* | Each user is given a directory in /home. Ordinary users write files only in their home directories. |
| */lib* | Contains shared library files used by the core system programs. |
| */lost+found* | It is used in the case of a partial recovery from a filesystem corruption event. In normal circumstances it is empty. |
| */media* | Will contain the mount points for removable media, such as USB drives that are mounted automatically at insertion. |
| */mnt* | On older Linux systems, the folder contains mount points for removable devices that have been mounted manually. |
| */opt* | Is used to install "optional" software, mainly commercial software products. |
| */proc* | It is a virtual filesystem maintained by the Linux kernel. The "files" it contains are peepholes into the kernel itself. |
| */root* | The home directory for the root account |
| */sbin* | Contains "system" binaries. These are programs that perform vital system tasks. |
| */tmp* | It is intended for storage temporary files created by various programs. |
| */usr* | The directory tree if likely the largest one on a Linux system. It contains all the programs and support files used by regular user. |
| */usr/bin* | Contains the executable programs installed by your Linux distribution. |
| */usr/lib* | The shared libraries for the programs in */usr/bin*. |
| */usr/local* | The */usr/local* tree is where programs that are not included with your distribution but are intended for system-wide use are installed. Programs compiled from source code are normally installed in */usr/local/bin*. |
| */usr/sbin* | Contains more system administration programs. |
| */usr/share* | Contains all the shared data used by programs in */usr/bin*, like default configuration files, icons, backgrounds, sound files, etc. |
| */usr/share/doc* | Contains documentation files organized by installed package. |
| */var* | The */var* directory tree is where data that is likely to change is stored. Various databases, spool files, user mail, etc. are located here. |
| */var/log* | Contains *log files*, records of various system activity. These are very important and should be monitored from time to time. |

## Symbolic Links

Notice the first letter `l` and the entry seems to have two filenames in the following example:

```console
lrwxrwxrwx   1 root root      20 Jan 12  2022 libzlcore.so.0.13 -> libzlcore.so.0.12.10
```

This is a s[ecial kind of a file called a *symbolic link* (*soft link* or *symlink*). It is possible to have a file referenced by multiple names.

This allows us to

- use common name without version for programs to reference to
- upgrade underline file that include with version number in its name
- recover to previous version of the file simply rewriting the symbolic link

### Hard links

There is a second type of link called a *hard link*. Hard links also allow files to have multiple names, but they do it in a different way.
