# Bandit Level 15 → 16

## Objective
Submit the password to port 30001 on localhost using SSL encryption.

## Tools Used
- `openssl s_client`

## Process
`openssl s_client -connect localhost:30001`

(Once connected, paste the current password).

## What I Learned
- Using SSL/TLS to communicate with encrypted network services.
