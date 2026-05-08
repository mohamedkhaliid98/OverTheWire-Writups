# Natas Level 11 → 12
 
## Objective
Upload a malicious PHP file to the server by manipulating a hidden form field, then execute it to read the password for Natas 13.
 
## Tools Used
 
* Browser Dev Tools (F12 — Elements/Inspector tab)

## Process
 
1. Opened the upload page and clicked F12 to open browser dev tools.
2. Found a hidden input field in the HTML form that controls the saved file's extension.
3. Changed the hidden field value from `.jpg` to `.php` directly in the Elements tab.
4. Uploaded a PHP file containing a system command instead of a real image.
5. Clicked the returned upload link — the server executed the PHP file and printed the password for Natas 13.

## What I Learned
 
* **Client-Side Trust:** Hidden form fields are fully visible and editable by the user — never use them to enforce server-side security decisions.
* **File Upload Validation:** Always validate uploads on the server side. Whitelist safe extensions, check MIME types, and never rely on the client to supply the filename or extension.
