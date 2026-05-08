# Natas Level 3 → 4

## Objective
Retrieve the password for Natas 5 by spoofing the HTTP Referer header using Burp Suite Repeater.

## Tools Used
- Burp Suite Community Edition (Repeater)

## Process
1. Intercepted the request to `natas4` and sent it to **Repeater** (`Ctrl+R`).
2. Located the `Referer: http://natas4.natas.labs.overthewire.org/` and manually changed the header to:
   `Referer: http://natas5.natas.labs.overthewire.org/`
3. Ensured the HTTP syntax was correct (space after colon, no space before, clean line at the end).
4. Clicked **Send** and monitored the **Response** pane on the right.
5. Scanned the HTML body of the response to find the cleartext password for the next level.

## What I Learned
- **Response Inspection:** In web penetration testing, the "view source" of the response often contains the data you need, even if the browser hasn't rendered it yet.
- **Statelessness of HTTP:** Every request is a fresh start. By using Repeater, I can modify a single request and see how the server reacts without affecting my actual browser session.
