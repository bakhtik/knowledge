# What is the shell?

- [A shell prompt](#a-shell-prompt)
- [Command history](#command-history)
- [Calendar command](#calendar-command)
- [Disk space and RAM amount commands](#disk-space-and-ram-amount-commands)
- [Ending a terminal session](#ending-a-terminal-session)

The *shell* is that passes commands to the operating system to catty out.

The most available shell program called *bash*, and acronym for *Bourne Again Shell*.

## A shell prompt

A *shell prompt* appears whenever the shell is ready to accept input.

```console
[username@hostname workdir]$
```

The hash mark (#) instead of a dollar sign ($) indicates that the terminal session has *superuser* privileges.

## Command history

Press `the up-arrow` key to see previously entered commands - the *command history*. By default Linux remembers the last 1000 commands (`echo $HISTSIZE`)

## Calendar command

Type `date` for display the current time and date.

```console
$ date
Thu Feb  1 09:39:53 AM +05 2024
```

Type `cal` to display a calendar of the current month.

```console
$ cal
   February 2024      
Su Mo Tu We Th Fr Sa  
             1  2  3  
 4  5  6  7  8  9 10  
11 12 13 14 15 16 17  
18 19 20 21 22 23 24  
25 26 27 28 29        
```

## Disk space and RAM amount commands

Enter `df` to get the current amount of free space on the disk drives.

```console
$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
tmpfs            4072588      2364   4070224   1% /run
efivarfs             246       113       129  47% /sys/firmware/efi/efivars
/dev/nvme0n1p7 498294164 404821188  68087608  86% /
```

Enter `free` to display the amount of free memory

```console
               total        used        free      shared  buff/cache   available
Mem:        40725848     4248152    32260400      704724     4217296    33188060
Swap:       33160692           0    33160692
```

## Ending a terminal session

Enter `exit` to end a terminal session.
