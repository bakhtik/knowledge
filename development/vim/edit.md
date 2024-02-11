# Edit in Vim

If you use `vim` command the editing occurs inside your command window.

```console
$ vim file.txt
```

The tilde (~) lines indicate lines not in the file.

The Vim editor is a modal editor, this it behaves differently in each mode.

Basic modes are:

- **Normal mode**: the characters you type are commands.
- **Insert mode**: the characters are inserted as text.
- **Command-line mode**: to enter complex commands.

Type the "i" command to start Insert mode.

Press the `<Esc>` to go back to Normal mode.

Type the ":" in Normal mode to enter the Command-line mode.

Use `set: showmode` command to see mode in the status line. If it's blank - you are in Normal mode.

## Deleting a line break

Use the `J` command to join two lines by pressing the on the first line.

## Getting out

To exit, use the `ZZ` command that writes the file and exits.

## Discarding changes

Type `:q!` to quit-and-throw-things-away.

## Finding help

Use `:help` to get generic help.

Press `ZZ` to exit the help.

Use `:help {subject}` to get help on a given subject.

Use `:help index` to get a complete index of all Vim commands.
