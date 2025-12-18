## Bandit Level 13 → Level 14

### Goal
Log in using an SSH private key.

### Approach
Use the provided private key for authentication.

### Solution
```bash
ssh -p 2220 -i ssh.private bandit14@bandit.labs.overthewire.org
```

### What I learned
- SSH key-based authentication
