# Bandit Level 16 → 17

## Objective
Find which port in the range 31000-32000 is listening and speaks SSL.

## Tools Used
- `nmap`, `openssl`

## Process
1. Scanned ports: `nmap -sV -p 31000-32000 localhost` 
used `-sV` to get the version of the ports and see who speaks SSL  
   
2. Once i found the open port, i submitted the password using `openssl s_client`.

## What I Learned
- Port scanning and service identification.
