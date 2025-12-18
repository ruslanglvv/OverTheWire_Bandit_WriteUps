## Bandit Level 12 → Level 13

### Goal
Extract a password from a repeatedly compressed file.

### Approach
Convert hex dump back to binary and recursively extract archives based on file type.

### Solution
```bash
xxd -r data.txt > data.bin
file data.bin
# extract based on detected file type
```

### What I learned
- Hexdump reversal
- Identifying and extracting compressed files
