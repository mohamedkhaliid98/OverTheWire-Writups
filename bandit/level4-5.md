# Bandit Level 4 → 5

## Objective
Find the only human-readable file in the `inhere` directory.

## Tools Used
- `file`
- `cat`

## Process
Used a wildcard with the `file` command to check the encoding of every file:
`file ./*`
Once the ASCII text file was identified, I read it with `cat`.

## What I Learned
- The `file` command is essential for identifying data types when filenames are misleading.
