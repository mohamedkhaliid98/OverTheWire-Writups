# Bandit Level 8 → 9

## Objective
Find the only line in `data.txt` that occurs exactly once.

## Tools Used
- `sort`
- `uniq -u`

## Process
`uniq` only detects duplicates in adjacent lines, so I sorted the file first:

`sort data.txt | uniq -u`

## What I Learned
- Piping multiple commands together and the requirement of `sort` for `uniq` to function properly.
