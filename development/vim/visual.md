# Visual Mode

## Grok Visual Mode

Visual mode allows us to select a range of text and then operate upon it.

Many of the Normal mode commands work just the same in Visual mode, like `h`, `j`, `k`, `l`, `f{char}`, `;`, `,`, etc.

Some Visual mode commands usage is used slightly differently, i.e. the `c` command. In normal mode we select the action, and then specify the range. In Visual mode it is vice versa.

## Define a visual selection

Visual mode's three submodes deal with different kinds of text

- *character-wise:* for working at the level of individual words or phrases
- *line-wise:* for operating on entire lines
- *block-wise:* to work with columnar regions of the document

### Enabling visual modes

The `v` key is our gateway into Visual mode.

| Command | Effect |
|---------|--------|
| `v` | Enable character-wise Visual mode |
| `V` | Enable line-wise Visual mode |
| `<C-v>` | Enable block-wise Visual mode |
| `gv` | Reselect the last visual selection |

### Switching between visual modes

| Command | Effect |
|---------|--------|
| `<Esc>` / `<C-[>` | Switch to Normal mode |
| `v`, `V`, `<C-v>` | Switch to Normal mode (when used from character-, line- or block-wise Visual mode, respectively) |
| `o` | Go to the end of highlighted text |

### Toggling the free end of a selection

The range of a Visual mode selection is marked by two ends: one end is fixed and the other moves freely with our cursor. We can use the `o` key to toggle the free end.
