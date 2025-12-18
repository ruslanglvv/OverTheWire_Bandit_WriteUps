### Goal
Extract human-readable strings from a file.

### Approach
Use `strings` to filter printable characters.

### Solution
```bash
strings data.txt | grep "="
```

### What I learned
- Using `strings` for binary analysis
- Filtering output with `grep`