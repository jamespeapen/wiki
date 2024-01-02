# Git

## Restoring a lost stash

Run:

```bash
git --log --oneline --decorate --all $( git fsck --no-reflog | awk '/dangling commit/ {print $3}' )
```


Look for an entry in the log starting with WIP whose diff matches the lost
stash, copy its has and run

```bash
git stash apply [hash]
```

The hash can also be found using the gitk gui:

```bash
gitk --all $( git fsck --no-reflog | awk '/dangling commit/ {print $3}' )
```

This will open a gitk window with a log.

From <https://stackoverflow.com/a/91795>.
