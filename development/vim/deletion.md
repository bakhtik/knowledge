# Deletions commands in VIM

- [Delete a word](#delete-a-word)
- [Delete to the end of the line](#delete-to-the-end-of-the-line)
- [On operators and motions](#on-operators-and-motions)
- [Using a count for a motion](#using-a-count-for-a-motion)
- [Using a count to delete more](#using-a-count-to-delete-more)
- [Operating on lines](#operating-on-lines)
- [The undo command](#the-undo-command)

All deletion operations store text in a Vim register, from there it can be taken again.

## Delete a word

Type `dw` to delete a word.

## Delete to the end of the line

Type `d$` to delete to the end of the line.

## On operators and motions

The format of the delete command:

```console
d motion
```

Where

- d: delete operator
- motion: what the operator will operate on

List of motions:

- w: until the start of the next word
- e: to the end of the current word
- $: to the end of the line

Note, pressing motion without operator with move cursor as specified.

## Using a count for a motion

Typing a number before a motion repeats it that many times.

```console
2e - two words forward
3w - end of the third word
0 (zero) - beginning of the line 
```

## Using a count to delete more

Typing a number with an operator repeats it that many times.

```console
d number motion
```

For example, `d2w` deletes two words.

## Operating on lines

Type `dd` to delete the whole line.

You can user form `number dd` to delete several consecutive lines, like `2dd`.

## The undo command

Press `u` to undo the previous actions, `U` to undo all changes on a line.

Press `CTRL-R` to redo the commands (undo the undo's)
