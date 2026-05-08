# Bandit Level 28 → 29

## Objective
Retrieve a password that has been masked or deleted in the current version of a Git repository.

## Tools Used
- `git log`
- `git log -p`
- `git show`

## Process
1. Cloned the repository as instructed in the previous level.
2. Observed that the current version of the README file contained `password: xxxxxxxxxx`.
3. Used `git log` to view the commit history of the repository.
4. Used `git log -p` to inspect the specific changes made in previous commits.
5. Found a commit where the actual password was removed/replaced and identified the original string in the "diff" output.

## What I Learned
- Git is a permanent record; "deleting" information in a new commit does not erase it from the history.
- Using `git log -p` and `git show` is essential for digital forensics and recovering overwritten data in version control.
