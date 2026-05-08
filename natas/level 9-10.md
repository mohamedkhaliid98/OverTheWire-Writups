# Natas Level 9 → 10

## Objective
Retrieve the Natas 11 password by bypassing a character filter in a command injection vulnerability.

## Details
- **Vulnerability:** Argument Injection (Grep Manipulation)
- **Filtered Characters:** `;`, `|`, `&`

## Tools Used
- Web Form Input

## Process
1. Observed that the common command separators (`;`, `|`, `&`) are now blocked by a regular expression.
2. Realized the `grep` command is executed as: `grep -i $key dictionary.txt`.
3. Exploited the fact that `grep` accepts multiple file arguments.
4. Input: `. /etc/natas_webpass/natas11`
5. The resulting server-side command became: `grep -i . /etc/natas_webpass/natas11 dictionary.txt`.
6. `grep` searched for any character (`.`) inside the password file and the dictionary file, printing the contents of both.

## What I Learned
- **Argument Injection:** Even if you can't "break out" of a command using separators, you can often change the command's behavior by adding extra arguments.
- **Incomplete Blacklisting:** Filtering specific characters (blacklisting) is usually less effective than only allowing specific characters (whitelisting). 
- **Grep Mechanics:** Understanding how standard Linux binaries handle multiple inputs is a powerful tool in a pentester's arsenal.
