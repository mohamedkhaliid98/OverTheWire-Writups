# Natas Level 8 → 9

## Objective
Retrieve the Natas 10 password by exploiting a Command Injection vulnerability.

## Details
- **Vulnerability:** OS Command Injection (Remote Code Execution)

## Tools Used
- Web Form Input

## Process
1. Analyzed the source code and found the `passthru()` function executing a shell command: `grep -i $key dictionary.txt`.
2. Realized that the `$key` variable (my input) was not being sanitized for shell metacharacters.
3. Crafted an input string to terminate the intended command and execute a new one.
4. Input: `; cat /etc/natas_webpass/natas10`
5. The resulting server-side command became: `grep -i ; cat /etc/natas_webpass/natas10 dictionary.txt`.
6. The server executed the `cat` command, printing the password file directly to the browser.

## What I Learned
- **Command Injection:** This occurs when an application passes unsafe user-supplied data to a system shell.
- **Input Sanitization:** Developers must use functions like `escapeshellarg()` or `escapeshellcmd()` in PHP to prevent users from breaking out of the intended command.
- **The Power of Semicolons:** In Bash/Linux, `;` is a command separator that allows for multiple unrelated commands to run sequentially.
