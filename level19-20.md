## Bandit Level 19 → Level 20

### Goal
Use a setuid binary to execute a command as another user and retrieve the password for the next level from /etc/bandit_pass.

### Approach
1. Identify the setuid binary located in the home directory.
2. Run the binary without arguments to understand how it works.
3. Execute a command through the setuid binary so it runs with the privileges of the next user.
4. Use this command execution to read the correct password file.

### Solution
```bash
    ./bandit20-do cat /etc/bandit_pass/bandit20
```
### What I learned
- How setuid binaries work in Linux
- The difference between real user ID and effective user ID
- How to execute a single command as another user without spawning an interactive shell
