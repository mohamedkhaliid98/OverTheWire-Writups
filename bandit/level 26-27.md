# Bandit Level 26 → 27

## Objective
Using `bandit27-do` to get the password of level 27.

## Tools Used
- `cat`
- `bandit27-do`

## Process
1. We know that the levels password are in `/etc/bandit_pass/`.
2. So we use `bandit27-do` to get the password.
3. Entered `./bandit27-do cat /etc/bandit_pass/bandit27`

## What I Learned
- How to use files with permission to another user to get what i need.
