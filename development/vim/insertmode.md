# Insert Mode

## Make corrections instantly from Insert Mode

Expert typists recommend drastic measure: delete the entire word; when type it out again.

| Keystrokes | Effect |
|------------|--------|
| `<C-h>` | Delete back one character (backspace) |
| `<C-w>` | Delete back one word |
| `<C-u>` | Delete back to start of the line |

## Get back to Normal Mode

We spend most of our time in Normal Mode, so it's important to be able to switch quickly between them.

| Keystrokes | Effect |
|------------|--------|
| `<Esc>` | Switch to Normal mode |
| `<C-[>` | Switch to Normal mode |
| `<C-o>` | Switch to Insert Normal mode |

### Meet Insert Normal Mode

In Insert Normal mode we can fire a single command, after which we'll be returned to Insert Mode immediately.

In example, we can use the `zz` command to redraw the screen with the current line in the middle of the window.

## Do back-of-the envelop calculations in place

The expression register allows us to perform calculations and then insert the result directly into our document.

| Keystrokes | Buffer Contents |
|------------|-----------------|
| `<C-r>={expression}<CR>` | Expression result wiil be inserted in the buffer |

## Insert unusual character by charecter code

Vim can insert any character by its numeric code.

| Keystrokes | Effect |
|------------|--------|
| `<C-v>{123}` | Insert character by decimal code |
| `<C-v>u{1234}` | Insert character by hexadecimal code |
| `<C-v>{nondigit}` | Insert nondigit literally |
| `<C-k>{char1}{char2}` | Insert character represented by `{char1}{char2}` digraph |
| `ga` | Shows the charachter code for the character under the cursor |
