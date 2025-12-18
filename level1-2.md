## Bandit Level 1 → Level 2

### Goal
Retrieve the password from a file named `-`.

### Approach
Files starting with `-` are treated as command-line options. To avoid this, the file path must be explicitly specified.

### Solution
```bash
cat ./-
```

### Explanation
Using `./-` tells the shell that `-` is a filename in the current directory, not stdin.

### What I learned
- How Linux interprets arguments starting with `-`
- How to safely access files with special names
