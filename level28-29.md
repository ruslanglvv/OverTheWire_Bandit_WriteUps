## Bandit Level 28 → Level 29

### Goal

Clone the provided Git repository and retrieve the password for the next level by analyzing the repository contents.


### Approach
1. Clone the Git repository provided in the level description.
2. Inspect the repository files and notice that the password is hidden.
3. Use Git history to investigate previous commits.
4. Identify the commit where the password was still present.
5. Check out that commit and read the password from the file.



### Solution
```bash
    # Create a temporary working directory
    mktemp -d
    cd /tmp/tmp.XXXXXX

    # Clone the repository
    git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
    cd repo

    # View commit history
    git log

    # Checkout the commit containing the password
    git checkout <commit_hash>

    # Read the password
    cat README.md
```


### What I Learned

- Git stores the full history of a repository, including deleted content.

- Sensitive information committed to Git can often be recovered later.

- it log allows inspection of commit history.

- git checkout <commit> can be used to view files from earlier states.

- Removing secrets from the current version does not erase them from Git history.