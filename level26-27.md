## Bandit Level 25 → Level 26

### Goal

Log in to `bandit26` using the provided SSH key and break out of the restricted shell.  
The shell for `bandit26` is not `/bin/bash`, so the objective is to identify what it is, understand how it works, and escape it to gain an interactive shell in order to access the next level.


### Approach

After logging in with the SSH private key, the connection immediately closes.  
This behavior indicates that the login shell is not a normal shell but a pager (`more`).

Key observations:
- `more` exits automatically if the output fits the terminal window
- If the output exceeds the screen size, `more` becomes interactive
- `more` allows opening the content in `vi`
- `vi` allows spawning a shell

To exploit this:
1. Force `more` to stay open by reducing terminal height
2. Enter `vi` from inside `more`
3. Set the shell to `/bin/bash`
4. Spawn a real shell
5. Use the provided setuid binary to read the next password


### Solution
```bash
    # Login using the SSH private key
    ssh -p 2220 -i bandit26.sshkey bandit26@bandit.labs.overthewire.org

    # (Resize terminal window to be very small before connecting)

    #Inside the pager (more), press:
    v

    # Inside vi, set a real shell
    :set shell=/bin/bash

    # Spawn the shell
    :shell

    # Verify access
    ls

    # Use the setuid binary to read the next password
    ./bandit27-do cat /etc/bandit_pass/bandit27

```


### What I Learned
- A user’s login shell does not have to be `/bin/bash`; it can be any executable, including pagers like `more`.
- The behavior of `more` depends on terminal size: if output fits the screen, it exits immediately; otherwise, it becomes interactive.
- Controlling the terminal (for example, resizing it) can be used to influence program execution.
- `more` allows opening its content in `vi` by pressing `v`.
- `vi` can be used to escape restricted environments by spawning a shell with `:shell`.
- The shell used by `vi` can be changed with `:set shell=/bin/bash`.
- Setuid binaries can be used to execute commands with elevated privileges in a controlled way.
- Understanding standard Unix tools deeply often reveals unintended escape paths in restricted setups.