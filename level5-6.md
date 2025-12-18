## Bandit Level 5 → Level 6

### Goal
Locate a file with specific properties.

### Approach
Use `find` with size, type, and permission filters.

### Solution
```bash
find inhere/ -type f -size 1033c ! -executable -exec file {} \; | grep ASCII
cat <path_to_file>
```

### What I learned
- Advanced usage of `find`
- Combining commands with pipes
