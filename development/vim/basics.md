# VIM Basics

- [Starting VIM](#starting-vim)
- [Moving the cursor](#starting-vim)
- [Moving the cursor](#moving-the-cursor)
- [Exiting VIM](#exiting-vim)
- [Text editing - deletion](#text-editing---appending) 
- [Text editing - inserting](#text-editing---insertion)
- [Text editing - appending](#text-editing---appending)
- [Editing a file](#editing-a-file)

## Starting VIM

```console
$ vim FILENAME <ENTER>
```

## Moving the cursor

To move the cursor, press h, j, k, l keys.

## Exiting VIM

Use `:q!` to exit VIM. This will trash all changes.

- Press `<ESC>` key
- Type: `q! <ENTER>`

Pressing `<ESC>` will place you in Normal mode or will cancel an unwanted and partially completed command.

## Text editing - deletion

Press `x` to delete the character under the cursor.

## Text editing - insertion

Press `i` to insert text before the cursor.

## Text editing - appending

Press `A` to append text after the line.

## Editing a file

Use `:wq` to save file and exit. This will save all changes.

