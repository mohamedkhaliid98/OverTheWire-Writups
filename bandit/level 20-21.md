# Bandit Level 20 → 21

## Objective
Use a SetUID binary to connect to a local port and exchange passwords.

## Tools Used
- `nc`, `&`

## Process
1. Set up a listener: `echo "bandit20_pass" | nc -l -p 1234 &`
2. Ran the binary: `./suconnect 1234`

## What I Learned
- Basic network handshaking and backgrounding processes.
