# Bandit Level 0 → 1

## Objective
Find the password stored in a file called readme in the home directory.

## Tools Used
- ssh
- ls
- cat

## Process
First I connected to the server using SSH:

ssh bandit0@bandit.labs.overthewire.org -p 2220

Listed the files in the directory:

ls

Saw a file called readme, read it:

cat readme

## What I Learned
- How to connect to remote servers using SSH
- Basic Linux file listing and reading
