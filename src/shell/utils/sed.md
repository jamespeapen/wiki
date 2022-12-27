# sed

### Remove all terminal escape sequences from input

```bash
[input] | sed "s,\x1B\[[0-9;]*[a-zA-Z],,g"
```
