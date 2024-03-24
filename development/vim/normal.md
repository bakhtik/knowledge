# Normal Mode

Normal mode is Vim's natural resting state, similar to having paint brushes off the canvas most of the time.

## Chunk your undoes

Control the granularity of the undo command.

The `u` key triggers the undo command, which reverts the most recent change, viz. anything that modifies the text in the document. In example `i{insert some text}<Esc>` constitutes a change.

From the moment we enter Insert mode until we return to Normal mode, everything we type (or delete) counts as a single change.

You can make each "undoable chunk" corresponding to a thought. In example, sentence wise chunks. 

Remember, that moving around in Insert mode *resets* the change.

## Compose Repeatable Changes

All three following keystrokes deletes a word under the cursor, but only last one, the `daw` (`delete a word`), is repeatable using the dot command.

```
db x  - delete backwards till beginning of the word, then the first character
b dw  - go to the beginning of the word, then delete a word
daw   - delete a word with spaces before the word
```

So the ability to repeat the meaning of the keystrokes combination can be used as a tie-breaker.

If you develop a habit of making your changes repeatable wherever possible, then Vim will reward you for it.
