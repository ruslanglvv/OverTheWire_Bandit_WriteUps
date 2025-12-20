## Bandit Level 17 → Level 18

### Goal
Find the password for the next level by identifying the only line that differs between
`passwords.old` and `passwords.new`.

---

### Approach
1. Compare the two files line by line.
2. Identify the line that was changed in `passwords.new`, since it contains the new password.

---

### Solution
```bash
    diff passwords.old passwords.new
```

The output shows the single line that differs between the two files.  
The changed line in `passwords.new` is the password for the next level.

---

### What I Learned
- How to compare files line by line using `diff`
- How to identify changes between two versions of a file
- Why using the simplest sufficient tool leads to clearer solutions
