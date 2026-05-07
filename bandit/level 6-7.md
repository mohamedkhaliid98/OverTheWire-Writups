# Bandit Level 6 → 7

## Objective
Find a file somewhere on the server that is owned by user `bandit7`, group `bandit6`, and 33 bytes in size.

## Tools Used
- `find`
- `2>/dev/null`

## Process
I searched from the root directory and redirected "Permission Denied" errors to `/dev/null` to keep the output clean:
`find / -user bandit7 -group bandit6 -size 33c 2>/dev/null`

## What I Learned
- Searching the entire filesystem and managing standard error (stderr) redirection.
