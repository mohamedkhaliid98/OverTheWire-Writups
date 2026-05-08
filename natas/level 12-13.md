# Natas — Level 12 → 13 
 
## Objective
Bypass a server-side image validation check by injecting PHP code into a real JPEG file, then execute it to read the password for Natas 14.
 
## Tools Used
 
* Burp Suite (Intercept & Repeater)
* A real JPEG image (small, under 1KB)
## Process
 
1. Opened the upload page — noticed it now rejects non-image files using `exif_imagetype()`.
2. Used a real small JPEG image to pass the image validation check.
3. Intercepted the upload request in Burp Suite.
4. Added the PHP payload at the very end of the image data in the request body.
5. Changed the filename extension from `.jpg` to `.php` in both filename fields in the request body.
6. Forwarded the request — the server saved the file as `.php`.
7. Clicked the returned upload link — the server executed the PHP and printed the password for Natas 14.
## What I Learned
 
* **Magic Bytes Bypass:** `exif_imagetype()` only checks the beginning of the file for a valid image signature — it does not scan the entire file, so PHP code appended at the end goes undetected.
* **Polyglot Files:** A file can be valid as two formats at once — a real image at the start and executable PHP code at the end. This is called a polyglot file.
* **Defense:** Never execute uploaded files regardless of their content. Store uploads outside the web root, strip metadata, and re-encode images server-side to remove any injected content.
