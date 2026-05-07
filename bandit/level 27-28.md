# Bandit Level 27 → 28

## Objective
Clone a remote Git repository from a local machine to retrieve the password for Level 28.

## Tools Used
- `git clone` (Local installation)
- `ls`
- `cat`

## Process
1. Initiated a clone of the remote repository using the SSH protocol and the specific port assigned to the Bandit wargame:
   `git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo`
2. Authenticated using the password previously discovered for user `bandit27`.
3. Navigated into the newly created `repo` directory.
4. Identified and read the `README` file, which contained the password for Level 28.

## What I Learned
- How to clone a Git repository using a full SSH URL, including a non-standard port.
- The importance of securing Git repositories, as they often contain sensitive information like passwords or API keys if not managed properly.
- Basic repository navigation and file inspection.
