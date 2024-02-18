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
