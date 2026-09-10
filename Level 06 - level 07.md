# Bandit Level 6 → 7

## Goal
Find a password stored **somewhere on the entire filesystem**, owned by user `bandit7`, group `bandit6`, and exactly **33 bytes** in size.

## Commands Used
```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat <filepath>
```

## Command Explanation
- `find / ...` → searches the **entire filesystem** starting from root (`/`)
- `-user bandit7` → only files owned by user `bandit7`
- `-group bandit6` → only files owned by group `bandit6`
- `-size 33c` → exactly 33 bytes
- `2>/dev/null` → redirects error messages (like "Permission denied") to nowhere, so the output stays clean
- `cat <filepath>` → prints the contents of the matched file

## Sample Output
```bash
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password

bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- `find` can search the whole filesystem, not just the current directory.
- Combining `-user`, `-group`, and `-size` filters helps pinpoint one exact file among thousands.
- Redirecting stderr (`2>/dev/null`) is essential when searching `/` since many folders throw permission errors.

## Issue I Faced
Without `2>/dev/null`, the terminal got flooded with "Permission denied" errors from restricted system folders, making it hard to spot the actual result.

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
