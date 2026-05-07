# Bandit Level 2 → 3

## Objective
Find the password in a file with spaces in its name.

## Tools Used
- `cat`
- '<' operator 
- '\' 

## Process
there was two problems that i ran into, number one was the file starts and ends with '--', number two was there's spaces in the file name which the shell cant read if i used 'cat' only

So after some searching and learning about filenames and how to read the spaces between also the '--'.

I used the operator '<' after cat with "\" before the spaces occur to tell the shell that there's a space in the name

it looked like this 'cat < --spaces\ in\ the\ filename--'

## What I Learned
- Handling spaces in filenames via '<' and '\'.
