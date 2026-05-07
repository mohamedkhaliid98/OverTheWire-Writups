# Bandit Level 13 → 14

## Objective
Use the provided SSH private key to log in as `bandit14`.

## Tools Used
- `ssh -i`

## Process
I used the `-i` flag to specify the identity file:
`ssh -i sshkey.private bandit14@localhost -p 2220`.

You would think that this would work, on the contrary, OverTheWire has stopped people from connecting within local host so i took the SSH private key saved it in my local machine in a notepad then used
`ssh -i "MyFileName" bandit14@localhost -p 2220`.

## What I Learned
- Private key authentication vs. password authentication.
