## Bandit Level 27 → Level 28

### Goal

There is a Git repository available over SSH.  
The task is to clone the repository and find the password for the next level inside it.

Repository:
ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo

The password for the user `bandit27-git` is the same as the password for `bandit27`.

### Approach

1. Create a temporary working directory to avoid permission issues.
2. Clone the Git repository using SSH and port `2220`.
3. Enter the cloned repository.
4. Inspect the repository contents.
5. Read the file containing the password for the next level.


### Solution
```bash
    # create a temporary directory
    mktemp -d
    cd /tmp/tmp.XXXXXXXX

    # clone the repository
    git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo

    # enter the repository
    cd repo

    # list files
    ls

    # read the file containing the password
    cat README
```


### What I Learned

- How to clone a Git repository over SSH using a non‑standard port.

- Git repositories can contain sensitive information in plain text.

- it is an important attack surface in security assessments.

- Using /tmp is a safe practice when working on restricted systems.

- Always inspect repository contents carefully, even if they look simple.