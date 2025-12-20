## Bandit Level 18 → Level 19

### Goal
Retrieve the password for the next level without opening an interactive shell,
because the `.bashrc` file forces an immediate logout on login.

---

### Approach
Instead of requesting an interactive shell, instruct SSH to execute a specific
command immediately after authentication. This allows reading the required file
without triggering the forced logout behavior.

---

### Solution
```bash
ssh -p 2220 bandit18@bandit.labs.overthewire.org cat readme
```

This command authenticates via SSH, executes `cat readme` remotely, prints the
password, and exits without starting an interactive shell.

---

### What I Learned
- How to execute remote commands over SSH without opening an interactive shell
- The difference between interactive SSH sessions and non-interactive command execution
- How shell startup files like `.bashrc` can affect login behavior
