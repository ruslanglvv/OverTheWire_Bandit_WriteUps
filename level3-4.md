## Bandit Level 3 → Level 4

### Goal
Find the hidden file containing the password.

### Approach
Hidden files are not shown by default. The `-a` flag reveals them.

### Solution
```bash
ls -a
cat ...Hiding-From-You
```

### What I learned
- How hidden files work in Linux
- Usage of `ls -a`
