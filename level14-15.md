## Bandit Level 14 → Level 15

### Goal
Send a password to a local service.

### Approach
Connect to the given port using netcat.

### Solution
```bash
nc localhost 30000
```

### What I learned
- Basic network communication with `nc`
