# Getting help in VIM

## Use online help system

To get access to Vim's comprehensive online help system:

- press the `<F1>` key, or
- type `:help`

Type `CTRL-W CTRL-W` to jump from one window to another.

Type `:q` to close the help window.

You can find help to a specific subject by giving the `help` command an argument.

```console
:help w
:help c_CRTL_D
:help user-manual
```

## Create a startup script

To start use more Vim features you should create a "vimrc" file.

1. Start editing the "vimrc" file:

    `:e ~/.vimrc`

2. Read the example "vimrc" file contents:

    `:r $VIMRUNTIME/vimrc_example.vim`

For more information type `:help vimrc-intro`

## Completion

You can use `CRTL-D` for command completion. Make sure Vim si not in compatible mode `:set nocp`.

Start writing a command then press `CTRL-D` for the list of matched commands.

Press `<TAB>` for command autocomplete.
