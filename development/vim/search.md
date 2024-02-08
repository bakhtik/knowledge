# Location and search in VIM

- [Cursor location and file status](#cursor-location-and-file-status)
- [The search command](#the-search-command)
- [Matching parentheses search](#matching-parentheses-search)
- [The substitute command](#the-substitute-command)

## Cursor location and file status

Type `CTRL-G` to show your location in the file and the file status.

Type `G` to move to the bottom of the file.

Type `gg` to move to the start of the file.

Type `<line number> G` to move to a specified line.

## The search command

Type `/` followed by a phrase to search for the phrase.

In Normal mode type `/<phrase> <ENTER>` to search for the phrase.

Type `n` to search for the phrase again.

Type `N` to search for the phrase in the opposite direction.

Type `?` instead of `/` to search in the backward direction.

Press `CTRL-O` to go back to where you came from.

Press `CTRL-I` to go forward.

When the search reaches the end of the file it will continue at the start, unless the 'wrapscan' option has been reset.

If you want to ignore case, use `\c`: `/phrase\c <ENTER>`

## Matching parentheses search

Type `%` to find a matching ), ], or } parentheses or brackets.

1. Place the cursor on any parentheses.
2. Type `%` character.
3. The cursor will move to the matching parenthesis or bracket.

This is very useful in debugging a program with unmatched parentheses.

## The substitute command

Type `:s/old/new` to substitute 'new' for 'old' in the first occurrence of 'old'.

Type `:s/old/new/g` to substitute 'new' for 'old' globally in the line.

Type `:#,#s/old/new/g` to substitute 'new' for 'old' globally in the range between specified line numbers.

Type `:%s/old/new/g` to substitute 'new' for 'old' globally in the file.

Type `:%s/old/new/gc` to substitute 'new' for 'old' globally in the file with prompt for every occurrence substitution.
