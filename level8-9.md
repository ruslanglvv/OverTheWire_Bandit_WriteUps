### Goal
Identify the only unique line in a file.

### Approach
Sort the file so identical lines are adjacent, then count occurrences.

### Solution
```bash
sort data.txt | uniq -c
```

### What I learned
- Why sorting is required before `uniq`
- Using pipes for command chaining