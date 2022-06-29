# File IO

## Removing trailing newlines

When pasting text into a terminal, the pasted text normally contains a newline
at the end. This can be removed with perl:

```bash
cat file.txt | perl -pe 'chomp if eof'
```

