# Natas Level 10 → 11

## Objective
Forge a cookie to set "showpassword" to "yes" by exploiting a weak XOR cipher.

## Tools Used
- Burp Suite (Decoder & Repeater)
- CyberChef (XOR Reversing)

## Process
1. Captured the session cookie `data` in **Burp Suite**.
2. Decoded the URL and Base64 formatting to get the raw encrypted bytes.
3. Exploited the XOR property: `Plaintext ^ Ciphertext = Key`.
4. XORed the default JSON `{"showpassword":"no","bgcolor":"#ffffff"}` with the raw cookie bytes to reveal the key.
5. Used the discovered key to XOR a new JSON string: `{"showpassword":"yes","bgcolor":"#ffffff"}`.
6. Re-encoded the new result into Base64 and updated the cookie in **Burp Repeater**.
7. Sent the request and received the password for Natas 12.

## What I Learned
- **XOR Vulnerability:** XOR encryption is completely transparent if the attacker knows any part of the original message (Known Plaintext Attack).
- **Cookie Integrity:** Never store sensitive logic or authorization flags in a client-side cookie without using strong, server-side signatures (like HMAC).
