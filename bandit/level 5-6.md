# Bandit Level 5 → 6

## Objective
Find a file in the `inhere` directory that is human-readable, 1033 bytes in size, and not executable.

## Tools Used
- `find`

## Process
I used the `find` command with specific flags to filter for the exact file requirements:

`find . -type f -size 1033c ! -executable`

## What I Learned
- Using `find` to filter by file size (`c` for bytes) and logical operators like `!` (not).
