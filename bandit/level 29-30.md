# Bandit Level 29 → 30

## Objective
Find a password hidden within Git tags after finding no leads in branches or commit history.

## Tools Used
- `git tag`
- `git show`

## Process
1. Cloned the repository and performed standard checks ( `git log`, `git branch -a`).
2. Found no password in the current files, history, or alternative branches.
3. Used the command `git tag` to check for any tagged release points in the repository.
4. Discovered a tag named `secret`.
5. Used `git show secret` to inspect the contents of that tag.
6. The password for the next level was revealed in the tag's metadata/content.

## What I Learned
- Git Tags are used to bookmark specific commits, often for versioning (e.g., v1.0).
- Information can be hidden in tags even if it's not visible in the current branch's head or history.
- `git show` is a versatile tool for inspecting various types of Git objects (commits, tags, etc.).
