# Manipulating Files and Directories

Here we will introduce the following commands:

- `cp` - Copy files and directories.
- `mv` - Move/rename files and directories. 
- `mkdir` - Create directories.
- `rm` - Remove files and directories
- `ln` - Create hard and symbolic links.

Complicated tasks can be easier with powerful and flexible command-line programs.

## Wildcards

*Wildcards* are the special characters to help you rapidly specify groups of filenames. Using wildcards (aka *globbing*) allows you to select filenames based on patterns of characters.

Table 1. *Wildcards*

| Wildcard | Matches |
|----------|---------|
| * | Any charachters |
| ? | Any single character |
| [*characters*] | Any character that is a memeber of the set *characters* |
| [!*characters*] | Any character that is not a memeber of the set *characters* |
| [[:*class*:]] | Any character that is a memeber of the specified *class* |

Table 2. *Commonly used character classes*

| Character Class | Matches |
|-----------|---------|
| [:alnum:] | Any alphanumeric character |
| [:alpha:] | Any alphabetic character |
| [:digit:] | Any numeral |
| [:lower:] | Any lowercase letter |
| [:upper:] | Any uppercase letter |

Table 3. *Wildcard Examples*

| Pattern | Matches |
|---------|---------|
| `*` | All files |
| `g*` | Any file beginning with *g* |
| `b*.txt` | Any file beginning with *b* followed by any characters and ending with *.txt* |
| `Data???` | Any file beginning with *Data* followed by exactly three characters |
| `[abc]*` | Any file beginning with either *a, b,* or *c* | 
| `BACKUP.[0-9][0-9][0-9]` | Any file beginning with `BACKUP.` followed by exactly three numerals | 
| `[[:upper:]]*` | Any file beginning with an uppercase letter | 
| `[![:digit:]]*` | Any file not beginning with a numeral | 
| `*[[:lower:]123]` | Any file ending with a lowercase letter or the numerals *1, 2,* or *3* | 

Wildcard can be used with any command that accepts filenames as arguments.

You should avoid using character ranges `[A-Z]` or `[a-z]` and use character classes instead.

## mkdir - Create directories

The `mkdir` command is used to create directories.

```console
mkdir directory...
```

`...` followed an argument means that the argument can be repeated, like `mkdir dir1 dir2 dir3`.

## cp - Copy files and directories

The `cp` command copies files and directories.

```console
cp item1 item2
```

To copy multiple items into a directory:

```console
cp item... directory
```

Table 4. cp Options

| Option | Meaning |
|--------|---------|
| -a, --archive | Copy files with original attirbutes. By default it uses attributes of the user performing the copy. |
| -i, --interactive | Prompt before overwriting an existing file. **`cp` silently overwrites files be default** |
| -r, --recursive | Recursively copy directories and thier contents. Option is required when copy directories. |
| -u, --update | Copy only non-existing or newer files. |
| -v, --verbose | Display informative messages as the copy is performed. |

## mv - Move and rename files

