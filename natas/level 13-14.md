## Level 13 -> 14 
 
**Objective**
Bypass a login form with no input sanitization by injecting SQL to make the query always return true, retrieving the password for Natas 15.
 
### Tools Used
 
* Browser `?debug` parameter

### Process
 
1. Opened the login page and viewed the source code — saw the PHP query was built by directly concatenating user input with no filtering.
2. Added `?debug` to the URL to see the raw SQL query being executed on each submit.
3. Tried single quote `'` first — query broke differently, confirming input lands inside double quotes `"`.
4. Injected into the **username** field, left password blank:
   ```
   " OR 1=1-- -
   ```
5. Submitted — the resulting query became always-true, returned all rows, and the server printed the password for Natas 15.
   
### What I Learned
 
* **SQL Injection:** Unsanitized user input concatenated directly into a query lets an attacker rewrite the query logic entirely.
* **Tautology Attack:** `OR 1=1` is always true — forces the database to return every row regardless of credentials.
* **Comment Injection:** `-- -` comments out the rest of the query, removing the password check completely.
* **Debug Parameters:** The `?debug` flag exposed the raw query — never leave debug output enabled in production.
* **Defense:** Use prepared statements / parameterized queries. Never build SQL strings from raw user input.
---
