# Bandit Level 22 → 23

## Objective
Reverse engineer a script that uses MD5 hashing to name its output file.

## Tools Used
- `echo`, `md5sum`

## Process
I reproduced the script's hash logic for the user `bandit22`:
`echo "I am user bandit22" | md5sum | cut -d ' ' -f 1`
Then I read the file in `/tmp/` named with that hash.

## What I Learned
- How deterministic hashing can be used for "hidden" filenames.
