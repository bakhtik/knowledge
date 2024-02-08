# Spell checking in VIM

- [Turn on spell checking](#turn-on-spell-checking)
- [Turn spell checking off](#turn-spell-checking-off)
- [Using spellchecking](#using-spellchecking)

## Turn on spell checking

```console
:set spell spelllang=en_us
```

Turn spell checking on *only* in the local buffer:

```console
:setlocal spell spelllang=en_us
```

## Turn spell checking off

```console
:set nospell
```

## Using spellchecking

`]s` - move cursor to the next misspelled word

`[s` - move cursor to the previous misspelled word

`z=` - show spelling alternatives

`zg` - add word to the dictionary

`zw` - mark word as incorrect
