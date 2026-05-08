# Natas Level 1 → 2

## Objective
Retrieve the password for Natas 3 by exploiting a Directory Listing vulnerability.

## Tools Used
- Browser Address Bar
- Manual URL Manipulation

## Process
1. Inspected the source code of the main page and found an image hosted at `/files/pixel.png`.
2. Noted that while the main page was empty, the presence of a `/files/` directory suggested further content might be available.
3. Navigated directly to the directory URL: `http://natas2.natas.labs.overthewire.org/files/`.
4. Observed that the server had "Directory Indexing" enabled, displaying a list of all files in that folder.
5. Found a text file (e.g., `users.txt`) sitting alongside the image.
6. Opened the text file to find a list of usernames and passwords, including the credential for `natas3`.

## What I Learned
- **Information Leakage:** Enabling directory listing on a web server is a major security risk, as it allows attackers to see the entire file structure and find sensitive files (like backups, logs, or configuration files) that aren't intended for public view.
- **URL Path Traversal:** Simply moving up one level in a URL path can often reveal hidden administrative or data folders.
