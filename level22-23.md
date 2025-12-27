## Bandit Level 22 → Level 23

### Goal
Obtain the password for the next level by analyzing a cron job and understanding how its script generates a temporary file containing the password.


### Approach
- Inspect the cron configuration directory `/etc/cron.d/` to locate the job related to this level.
- Read the cron configuration to determine which script is executed and under which user.
- Analyze the script logic to understand how it constructs the output filename.
- Reproduce the same logic manually to determine the correct filename.
- Read the password from the generated file in `/tmp`.

### Solution
```bash
    cd /etc/cron.d/
    ls
    cat cronjob_bandit23
    cat /usr/bin/cronjob_bandit23.sh
    echo "I am user bandit23" | md5sum
    cat /tmp/8ca319486bfbbc3663ea0fbe81326349
```

### What I Learned
- Cron jobs can execute scripts periodically as specific users.
- Reading and understanding shell scripts written by others is critical for security analysis.
- Hash functions like `md5sum` are often used to generate deterministic but non-obvious filenames.
- Hashing predictable input does not provide security if the logic can be reproduced.
- Automated jobs can leak sensitive data through predictable side effects.