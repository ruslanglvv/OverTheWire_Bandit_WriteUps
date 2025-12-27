## Bandit Level 20 → Level 21

### Goal
Send the password from the previous level to the provided setuid binary over a local TCP connection in order to receive the password for the next level.

### Approach
- Start a local TCP listener on a chosen port using `nc`
- Pipe the previous level password into the listener
- Run the setuid binary so it connects to the listener and validates the password
- Keep the listener running in the background so both processes can interact

### Solution
```bash
    echo "{password}" | nc -l 2000 &
    ./suconnect 2000
```

### What I Learned
- How to create a TCP listener using `nc`
- How standard input can be piped into a network socket
- How background processes allow simultaneous program interaction
- How a setuid binary can act as a client and communicate over the network
