# Bandit Level 14 → 15

## Objective
Submit the password of the current level to port 30000 on localhost.

## Tools Used
- `nc` (netcat)

## Process
echoed the current password for this level to port 30000 on local host.

`echo "current_password" | nc localhost 30000`

## What I Learned
- Interacting with network services via raw TCP connections.
