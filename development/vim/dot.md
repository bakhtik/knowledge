# The Dot Strategy in VIM

Our ideal: one keystroke to move, one keystroke to execute

## The Dot Command is a Micro Macro

The dot command lets us repeat the last change, that is every keystroke we did from the moment we enter Insert mode until we return to Normal mode.

Note that moving around in Insert mode resets the change.

## Don't repeat yourself

Appending ";" at the end of the lines:

1. Make the change: `A;<Esc>`
2. Move to the next line and repeat the change: `j.` 
3. Repeat as much as needed: `j.j.j.`

## Take one step back, then three forward

Appending spaces around plus sign:

1. Find the plus sign character: `f+` 
2. Make the change: `s_+_<Esc>`
3. Repeat the search and repeat the change: `;.`

`f{char}` is looking ahead for the next occurrence of the specified character.

`s` deletes the character under the cursor and then enters Insert mode.

`;` repeats the last search that the 'f' command performed.

## Act, Repeat, Reverse

Whenever Vim makes it easy to repeat an action or a motion, it always provides some way of backing out.

Repeatable actions and how to reverse them:

| Intent | Act | Repeat | Reverse |
|--------|-----|--------|---------|
| Make a change | {edit} | `.` | `u` |
| Scan the line for next character | `f{char}`/`t{char}` | `;` | `,` |
| Scan the line for previous character | `F{char}`/`T{char}` | `;` | `,` |
| Scan the document for next match | /pattern`<CR>` | `n` | `N` |
| Scan the document for previous match | ?pattern`<CR>` | `n` | `N` |
| perform substitution | `:s/target/replacement` | & | u |
| Execute a sequence of changes | `qx{changes}q` | `@x` | 'u' |

## Find and replace by hand

Change the first occurrence by hand and then find and replace every other match one by one.

Alternative to this is to globally replace the match in the file using command `:%s/old/new/g`.

### Be lazy: search without typing

1. Place the cursor on the word and hit the `*` key.
2. Replace the word: `cw{new word}<Esc>`
3. Find next occurrence of the match: `n`
4. Replace, if needed: `.`
5. Repeat and change if needed: `n.n.n.`

`*` searches forward for the keyword under the cursor on next to the cursor.

`cw` changes the word under the cursor without including following space.

`n` moves to the next occurrence of the match.
