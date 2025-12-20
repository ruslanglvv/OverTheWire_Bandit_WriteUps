## Bandit Level 16 → Level 17

### Goal
Submit the current level’s password to the only service that responds correctly on `localhost`,
listening on a port in the range 31000–32000, in order to obtain the credentials for the next level.

---

### Approach
1. Scan the specified port range on `localhost` to identify open ports.
2. Interact with each open port to determine whether the service expects plain TCP
   or TCP wrapped in SSL/TLS.
3. Identify the service that behaves differently from simple echo services.
4. Send the current level’s password to the correct service using the appropriate protocol.

---

### Solution
```bash
nmap localhost -p 31000-32000
# discover open ports in the given range

ncat localhost 31046
# send test input to check if the service accepts plain TCP

ncat localhost --ssl 31790
# connect to the service that expects SSL/TLS and send the password
```

By observing how each service responds to plain and encrypted connections,
it is possible to identify the correct one and retrieve the credentials
for the next level.

---

### What I Learned
- How to enumerate open ports on a local machine
- How to distinguish between plain TCP services and services that require SSL/TLS
- Why matching the correct protocol to a service is critical in network-based challenges
