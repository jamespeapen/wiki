# Shell bindings

These bindings allow editing input in the shell and searching through history.

## Emacs bindings

The default bindings are those found in the emacs editor and use Control and Alt
as modifiers to send commands.

### Navigation

**C**: control

**M**: Meta or Alt

- C-a: move to beginning of line
- C-e: move to end of line
- C-f: move forward one character
- C-b: move backward one character
- M-f: move forward one word
- M-b: move backward one word

### Deletion

- C-h: delete one character back
- C-d: delete one character forward
- C-k: delete everything in front of cursor
- C-w: delete one word backwards
- M-d: delete one word forwards
- C-u: clear line
- C-l: clear screen (not including current line)

### Alternatives

- C-m: return
- C-i: tab

### History

- C-p: move up in history
- C-n: move down in history
- C-r: search backward in history (best with `fzf`)
- C-s: search forward in history

## Vim bindings

Adding `set -o vi` in `.bashrc`or `inputrc` sets vim keybindings in the shell
and other shell based interfaces like the python REPL.  For zsh use `bindkey
-v`.

An indicator of the current mode can be shown in `bash >= 4.4`.

In `normal` mode, typing `v` opens the current shell input in vim.  The default
escape key or sequence can be changed using `bind` or `bindkey`. On the Colemak
layout I use ',m'.

```bash
# bash 
bind '",m":"\e"'

# zsh 
bindkey -e ,m \\e 
```
