# Bandit Level 1 → 2

## Objective
Find the password in a file named `-`.

## Tools Used
- `cat`

## Process
The dash `-` is usually interpreted by commands as "stdin". To read it as a filename, I used the relative path:
`cat ./-`

## What I Learned
- How to handle special characters in filenames using path references.
