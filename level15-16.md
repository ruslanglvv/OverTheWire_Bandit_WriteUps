## Bandit Level 15 → Level 16

### Goal
Establish a secure SSL connection.

### Approach
Use OpenSSL to connect to the service.

### Solution
```bash
openssl s_client -connect localhost:30001
```

### What I learned
- Basics of SSL/TLS connections