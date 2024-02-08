# Copy and insert in VIM

## The open command

Type `o` to open a line *below* the cursor and place you in the Insert mode.

Type `O` to open a line *above* the cursor and place you in the Insert mode.

## The append command

Type 'a' to insert text *after* the cursor.

You can press `e` to move to the end of the incomplete word and then `a` to complete it.

Note. `i`, `a`, and `A` all go to the Insert mode.

## Another way to replace

Type `R` to replace more than one character.

Replace mode is like Insert mode, but every typed character deletes an existing character.

## Copy and paste text

Use `y` operator to copy the text and `p` operator to paste it.

Press `yw` to yank the word.

Press `yy` to yank the whole line.

## Set option

Typing `:set xxx` sets the option 'xxx'. Some options are:

- `ic` `ignorecase`     ignore upper/lower case while searching
- `is` `incsearch`      show partial matches for a search phrase
- `hls` `hlsearch`      highlight all matching phrases

Prepend `no` to switch the option off: `:set noic`
