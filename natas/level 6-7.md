# Natas Level 6 → 7

## Objective
Retrieve the Natas 8 password using a Local File Inclusion (LFI) vulnerability.

## Details
- **Hint:** `<!-- hint: password for webuser natas8 is in /etc/natas_webpass/natas8 -->`

## Tools Used
- URL Manipulation (GET parameters)

## Process
1. Discovered an HTML comment in the source code providing the absolute path to the next level's password.
2. Observed the website's navigation structure: `index.php?page=[filename]`.
3. Identified that the `page` parameter is likely passed to a PHP `include()` or `readfile()` function without proper sanitization.
4. Replaced the `page` value with the absolute path from the hint:
   `http://natas7.natas.labs.overthewire.org/index.php?page=/etc/natas_webpass/natas8`
5. The server executed the request and printed the contents of the password file directly onto the webpage.

## What I Learned
- **Local File Inclusion (LFI):** A vulnerability where an application allows a user to submit input that is used to build a path to a file that is then included/read by the server.
- **Directory Traversal/Absolute Paths:** If an input is not "sandboxed," an attacker can access sensitive system files (like `/etc/passwd`) or application credentials.
- **Input Validation:** Parameters used for file operations must be strictly validated against a whitelist of allowed files.
