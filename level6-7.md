## Bandit Level 6 → Level 7

### Goal
Find a file owned by specific user and group.

### Approach
Search the entire filesystem while suppressing permission errors.

### Solution
```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat <path_to_file>
```

### What I learned
- File ownership concepts
- Redirecting error output