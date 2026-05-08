# Bandit Level 31 → 32

## Objective
Create and push a specific file to a remote Git repository to trigger a server-side hook that reveals the next password.

## Tools Used
- `git add -f`
- `git commit`
- `git push`
- Windows CMD (`set /p`)

## Process
1. Cloned the repository and identified the requirements in the `README.md`.
2. Encountered a `.gitignore` rule blocking `.txt` files; bypassed this using `git add -f key.txt`.
3. Faced a "Wrong!" rejection from the server due to Windows adding hidden CRLF line endings (making the file 15-16 bytes instead of the required 14 bytes).
4. Resolved the encoding issue by using the Windows command:
   `<nul set /p ="May I come in?" > key.txt`
5. Verified the file was exactly 14 bytes (no trailing spaces or newlines).
6. Reset the local branch to match the server (`git reset --hard origin/master`) to ensure a clean push.
7. Committed the correct file and pushed to the remote: `git push origin master`.
8. Captured the password for Level 32 from the `remote:` output in the terminal.

## What I Learned
- **Pre-receive Hooks:** Servers can use Git hooks to validate data before accepting a push.
- **Line Ending Sensitivity:** Linux servers expect LF (`\n`), while Windows defaults to CRLF (`\r\n`). In security challenges, even one extra hidden byte will cause a failure.
- **Byte-Perfect Creation:** Using `set /p` in Windows is a reliable way to create files without the automatic newline characters added by `echo`.
