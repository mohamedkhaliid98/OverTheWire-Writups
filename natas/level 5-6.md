# Natas Level 6 → 7

## Objective
Find a hidden secret stored in an included file and submit it via a POST request.

## Details
- **Vulnerability:** Information Leak / Improper File Access

## Tools Used
- Browser Address Bar
- View Source (`Ctrl+U`)

## Process
1. Inspected the provided PHP source code on the main page.
2. Noticed the line `include "includes/secret.inc";`, which indicates the secret is stored in a separate file.
3. Navigated directly to the include path: `/includes/secret.inc`.
4. Viewed the page source of the include file to retrieve the secret string.
5. Returned to the main Natas 6 page and entered the secret into the submission form.
6. Submitted the form to receive the password for Natas 7.

## What I Learned
- **Insecure File Storage:** Sensitive data (like secrets or configuration constants) should not be stored in files that are web-accessible.
- **Include Files:** Developers often use `.inc` or `.php` files to store variables. If the server isn't configured to hide these, anyone can read their contents.
- **Code Review:** Reading the logic of a PHP script (when provided) is essential for understanding what parameters the server is expecting.
