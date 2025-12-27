## Bandit Level 21 → Level 22

### Goal
Find the password for the next level by analyzing a program that is executed automatically by cron and identifying where it stores its output.


### Approach
- Inspect the cron configuration directory `/etc/cron.d/` to find jobs related to the current level.
- Read the cron configuration file to determine which script is executed, how often, and as which user.
- Locate and inspect the referenced script to understand its behavior.
- Identify any files created or modified by the script and check their permissions.
- Read the file where the password is written.

### Solution
```bash
    cd /etc/cron.d/
    ls
    cat cronjob_bandit22
    cat /usr/bin/cronjob_bandit22.sh
    cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

### What I Learned
- Cron jobs can run commands automatically at fixed intervals or on system events like reboot.
- Cron configuration files specify the execution schedule, user, and command.
- Output redirection to `/dev/null` hides command output but not side effects.
- Privileged cron jobs can unintentionally leak sensitive data through world-readable files.
- Inspecting scripts executed by cron is an effective way to discover hidden automation behavior.