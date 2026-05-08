# Natas Level 0 → 1

## Objective
Retrieve the password for Natas 2 by inspecting the source code when right-clicking is disabled.

## Details
- **Challenge:** The page has disabled the right-click context menu to prevent "View Source."

## Tools Used
- Browser Shortcuts (`Ctrl+U`)
- URL Manipulation (`view-source:`)
- **OR**: Developer shortcut (`F12`)
  
## Process
1. Authenticated into Natas 1 using the password found in Level 0.
2. Attempted to right-click to view the source, but the action was blocked by a JavaScript "Right-click disabled" alert.
3. Bypassed this restriction using the keyboard shortcut **`Ctrl+U`** (Windows/Linux) or **`Cmd+Option+U`** (Mac).
4. Alternatively, prepended the URL with `view-source:` in the address bar: 
   `view-source:http://natas1.natas.labs.overthewire.org`
5. Found the HTML comment containing the password for Natas 2.

## What I Learned
- **Security through Obscurity:** Disabling right-click is a classic example of "Security through Obscurity." It does not provide real security; it only creates a minor hurdle for the user.
- **Client Control:** The client (the user) has ultimate control over how their browser renders and displays the code sent by the server.
