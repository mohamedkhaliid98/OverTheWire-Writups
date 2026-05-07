# Bandit Level 11 → 12

## Objective
The password is in `data.txt` where all letters have been rotated by 13 positions (ROT13).

## Tools Used
- `tr`

## Process
I used the translate command to shift the alphabet positions:

`cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'`

## What I Learned
- Simple substitution ciphers and using `tr` for character mapping.
