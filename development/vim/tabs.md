# Tabs and spaces

The `tabstop` specifies the width of a Tab character.

The `expandtab` when enabled causes spaces to be uses instead of tab charater.

The `softtabstop` when enabled fine tunes the amount of white spaces to be inserted.

The `shiftwidth` determine the amount of white spaces to insert or remove using identeation commands in Normal mode.

If you prefer to work with tab characters then use `tabstop == softtabstop`.

If you prefer to work with spaces, then it is preferavel to use `softtabstop == shiftwidth`.

The most convenent setting is 

```
tabstop == softtabstop == shiftwidth
```

For example,

```
set ts=4 sts=4 sw=4 expandtab
```
