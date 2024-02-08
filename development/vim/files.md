# Files and external commands in VIM

- [How to execute an external command](#how-to-execute-an-external-command)
- [More on writing files](#more-on-writing-files)
- [Selecting text to write](#selecting-text-to-write)
- [Retrieving and merging files](#retrieving-and-merging-files)

## How to execute an external command

Type `:!<command>` to execute an external shell command.

You can execute external commands with arguments this way.

## More on writing files

Type `:w FILENAME` to save the changes made to the current Vim file to disk with name FILENAME.

## Selecting text to write

To save part of the text, type `v motion :w FILENAME`:

1. Select part of the text with `v motion`.
2. Press `:`, At the bottom of the screen :'<,'> will appear.
3. Type `w FILENAME` and press `<ENTER>` to save the selected text into a file.

Pressing `v` starts Visual selection. You can select text blocks and manipulate with them using operators like `d`.

## Retrieving and merging files

Type `:r FILENAME` to insert the contents of a file below the cursor position.

Type `r: !<command>` to read the output of an external command and put it below the cursor.
