# Manage multiple files
Vim lets us work on multiple files at the same time - the buffer list lets us keep track of opened files
- `:arg` command allows us to group files into a collection
- Vim allows us to split windows

## Track open files with the buffer list

We are not editing a file. Instead, we're editing an in-memory representation of a file, which is called a *buffer*.

Files are stored on the disk, whereas buffers exist in memory. If we decide that we want to keep our changes, we can write the contents of the buffer back into the file. Most Vim commands operate on buffers, but a few operate on files, including `:write`, `:update`, and `:saveas` commands.

The `:ls` command gives us a listing of all the buffers that have been loaded into memory:

```:ls
  1 %a   "a.txt"                        line 1
  2 #    "b.txt"                        line 1
```

`%` - buffer in the current window

`a` - an active buffer; it is loaded and visible

`#` - the alternate buffer for ":e #" and CTRL-^

You can quickly toggle between the current and alternate files by pressing `<C-^>`.

| Buffer action | Command |
|----------------|-----------|
| Move backward  | `:bprev`  |
| Move forward   | `:bnext`  |  
| Jump to the start  | `:bfirst` |
| Jump to the end  | `:blast` |
| Jump to a buffer by number | `:buffer N` |
| Jump to a buffer by name | `:buffer {bufname}` |

The `:bufdo` command allows us to execute as Ex command in all of the buffers.

### Deleting buffers

You can delete a buffer by using one of these forms:

```
:bdelete N1 N2 N3  (i.e. :bd 5 6 7 8 9 10)
:N,M bdelete	   (i.e. :5,10bd)
```

Note that deleting a buffer has no effect on its associated file; it simply removes the in-memory representation.

Unless you have a good reason to delete a buffer, you can don't bother at all.

## Group buffers into a collection with the argument list

The argument list is useful for grouping together a collection of files for easy navigation.

The argument list `:arg` represents the list of files that was passed as an argument when we ran the `vim` command.
The `[]` characters indicate which of the files in the argument list is active.

### Populate the argument list

We can set the contents of the argument list using the form:

```
:args {arglist}
```

For example

```
:args index.html app.js	// explicit filenames
:args *.*		// globes
:args **/*.js **/*.css	// globes, where ** looks recursevely into directories below
:args **/*.*
:args `cat .files`	// backtick expansion (".file" can contain a filename per line)
```

We can use the argument list to group our buffers into a collection. With the `:args {arglist} command, we can clear the list and then repopulate it from scratch.

| The argument list action | Command |
| ------------------------ | ------- |
| Move forward | `:next` |
| Move backward | `:prev` |
| Jump to the first file | `:first` |
| Jump to the last file | `:last` |
| Add file to the list | `:arga {arglist}` |
| Remove file from the list | `:argd {arglist}` |