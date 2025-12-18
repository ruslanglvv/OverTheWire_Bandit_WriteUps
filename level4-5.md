## Bandit Level 4 → Level 5

### Goal
Find the password among multiple files.

### Approach
Inspect file contents to identify readable text.

### Solution
```bash
file ./*
cat <identified_file>
```

### What I learned
- Using `file` to identify file types
- Filtering relevant files
