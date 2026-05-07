# Bandit Level 19 → 20

## Objective
Use a SetUID binary to read the password file for Level 20.

## Tools Used
- `./bandit20-do`

## Process
`./bandit20-do cat /etc/bandit_pass/bandit20`

## What I Learned
- Understanding how SetUID allows executing a file with the permissions of the file owner.
