# Bandit Level 25 → 26

## Objective
Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

## Tools Used
- `ssh -i`
- `vi`

## Process
1. Located the `bandit26.sshkey` in the home directory of `bandit25`.
2. Copied the SSHkey and saved it on my local machine as a key file not a txt one.
3. Connected via SSH: `ssh -i bandit26.key bandit26@bandit.labs.overthewire.org -p 2220`
4. It logged me out instantly after succesfully logging in.
5. saw that bandit26 was running on a `more shell` not regular shell. 
6. Shrunk the terminal window to force the `more` command to pause upon login.
7. Connected via SSH: `ssh -i bandit26.key bandit26@bandit.labs.overthewire.org -p 2220`.
8. At the `--More--` prompt, pressed `v` to open Vi.
9. Escaped to a full shell using `:set shell=/bin/bash` and `:shell`.

## What I Learned
- Bypassing restricted shells by exploiting the interactive features of paginators.
