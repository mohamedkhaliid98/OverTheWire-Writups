# Bandit Level 9 → 10

## Objective
Find human-readable strings in the binary file `data.txt`.

## Tools Used
- `strings`
- `grep`

## Process
I extracted ASCII strings from the binary and looked for several '=' characters, which usually denote the password line:

`strings data.txt | grep "=="`

## What I Learned
- Using `strings` to analyze binary or non-text files for useful information.
