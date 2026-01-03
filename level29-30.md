## Bandit Level 29 → Level 30

### Goal
There is a Git repository available over SSH.  
The task is to clone the repository and find the password for the next level (`bandit30`).

The challenge is that the password is **not located in the default branch**.



### Approach

1. Clone the Git repository using the provided SSH address and credentials.
2. Inspect the repository contents — the default `master` branch does **not** contain the password.
3. Enumerate all branches, including remote branches.
4. Switch to non-default branches and inspect their contents.
5. Locate the branch that contains sensitive information.
6. Read the password for the next level.


### Solution
```bash
    git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
    cd repo

    git branch -a

    git switch dev

    cat README.md

```


### What I Learned

- Git repositories can contain **multiple branches** with very different contents.
- The default branch (`master` / `main`) does **not always** contain all information.
- Sensitive data such as passwords is often accidentally left in:
  - `dev` branches  
  - feature branches  
  - testing or staging branches
- The command `git branch -a` is essential to enumerate **local and remote branches**.
- `git switch <branch>` (or `git checkout <branch>`) allows inspecting other branches safely.
- Reviewing Git history and branches is a common **real-world security issue** where secrets leak outside production.
- Git challenges often test **source code awareness**, not just basic commands.
