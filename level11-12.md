## Bandit Level 11 → Level 12

### Goal
Decode a ROT13-encoded message.

### Approach
Use `tr` to translate characters.

### Solution
```bash
tr 'N-ZA-Mn-za-m' 'A-Za-z' < data.txt
```

### What I learned
- Character substitution ciphers
- Input redirection in Linux
