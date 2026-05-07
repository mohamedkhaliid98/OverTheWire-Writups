# Bandit Level 18 → 19

## Objective
Log in as `bandit18`, bypassing a `.bashrc` that logs the user out.

## Tools Used
- `ssh` command execution

## Process
I executed the command through the SSH connection directly:
`ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"`

## What I Learned
- Running remote commands without spawning an interactive shell.
