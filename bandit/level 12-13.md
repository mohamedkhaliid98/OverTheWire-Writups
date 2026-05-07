# Bandit Level 12 → 13

## Objective
Extract the password from a file that has been repeatedly compressed.

## Tools Used
- `xxd`, `file`, `gzip`, `bzip2`, `tar`

## Process
1. Reverted the hex dump: `xxd -r data.txt > data`
2. Repeatedly checked the file type: `file data`
3. Renamed and decompressed based on type (e.g., `mv data data.gz && gunzip data.gz`) until the ASCII text was revealed.

## What I Learned
- Analyzing file headers and dealing with nested compression.
