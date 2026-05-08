# Natas Level 7 → 8

## Objective
Retrieve the password for Natas 9 by reversing a custom encoding function.

## Details
- **Vulnerability:** Weak Custom Cryptography (Obfuscation)

## Tools Used
- Online Tools (CyberChef)

## Process
1. Inspected the PHP source code provided on the page.
2. Identified the encoding logic used to protect the secret:
   `bin2hex(strrev(base64_encode($secret)))`
3. Obtained the `$encodedSecret` value from the source: `3d3d354c7a4b6473644c6d4c61464b61`.
4. Performed the reverse operations in order:
    * **Hex to String:**
    * **Reverse String:**
    * **Base64 Decode:** Resulting in the original secret.
5. Entered the decoded secret into the form on the Natas 8 page.
6. Submitted the form to retrieve the password for Natas 9.

## What I Learned
- **Encoding is not Encryption:** Encoding (Base64, Hex) is meant for data formatting, not security. Anyone who knows the encoding method can easily reverse it.
- **Obfuscation:** Reversing a string or shuffling data is "security through obscurity" and offers no real protection against a determined attacker.
- **Crypto Principles:** Never roll your own "encryption" functions; use industry-standard, proven cryptographic libraries.
