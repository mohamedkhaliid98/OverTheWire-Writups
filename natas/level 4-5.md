# Natas Level 4 → 5

## Objective
Gain access to the protected page by manipulating browser cookies.

## Details
- **Error:** "You are not logged in"

## Tools Used
- Burp Suite (Repeater) or Browser Developer Tools (Storage Tab)

## Process
1. Accessed the site and observed that the server denied access based on login status.
2. Inspected the HTTP request/response and identified a cookie named `loggedin`.
3. Observed that the cookie value was set to `0` (False).
4. Modified the cookie value to `1` (True) in the request headers using Burp Repeater.
5. Sent the modified request to the server.
6. The server accepted the spoofed session state and displayed the password for Natas 6.

## What I Learned
- **Cookie Manipulation:** Cookies are client-side storage. Since the user can edit them, they should never be used as the sole proof of authentication without server-side secrets (like signed JWTs or session IDs).
- **Session States:** Many older or poorly designed apps use simple "flags" (like `admin=1` or `loggedin=true`) to control access, which are extremely easy to bypass.
