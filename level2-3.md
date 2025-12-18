## Bandit Level 2 → Level 3

### Goal
Read a file that contains spaces in its name.

### Approach
Files with spaces must be quoted or escaped to be accessed correctly.

### Solution
```bash
cat "spaces in this filename"
# or
cat spaces\ in\ this\ filename
```

### What I learned
- How to handle filenames with spaces
- Difference between quoting and escaping
