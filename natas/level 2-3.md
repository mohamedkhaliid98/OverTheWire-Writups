# Natas Level 2 → 3

## Objective
Retrieve the password for Natas 4 by finding a hidden directory specified in the site's crawler instructions.

## Tools Used
- Browser Address Bar
- Manual URL Manipulation

## Process
1. Accessed the Natas 3 page and found no visible clues in the HTML source code.
2. Recalled that web developers use a standard file to prevent search engine spiders from indexing specific directories.
3. Navigated to the root file: `http://natas3.natas.labs.overthewire.org/robots.txt`.
4. Observed a "Disallow" entry in the file pointing to a hidden directory (e.g., `/s3cr3t/`).
5. Navigated to that hidden directory in the browser.
6. Found a `users.txt` file within the directory containing the password for Natas 4.

## What I Learned
- **Robots.txt:** While intended to guide search engines, this file often acts as a "map" for attackers by explicitly listing the locations of sensitive or hidden folders.
- **Hidden is not Secure:** Relying on the fact that a folder isn't "linked" anywhere is a form of weak security that is easily bypassed.
