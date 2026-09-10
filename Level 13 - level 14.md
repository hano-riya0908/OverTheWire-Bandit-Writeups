# Bandit Level 13 → 14

## Goal
An SSH private key (`sshkey.private`) is provided to log in directly as user `bandit14`, without needing a password.

## Commands Used
```bash
ls
chmod 600 sshkey.private
ssh -i sshkey.private bandit14@localhost -p 2220
cat /etc/bandit_pass/bandit14
```

## Command Explanation
- `ls` → lists files in the home directory to confirm `sshkey.private` is present
- `chmod 600 sshkey.private` → changes file permissions so only the owner can read/write the key (`600`); SSH refuses to use keys that are too open/world-readable
- `ssh -i sshkey.private bandit14@localhost -p 2220` → connects via SSH using a **private key file** (`-i`) for authentication instead of a password, logging in as `bandit14` on `localhost` port `2220`
- `cat /etc/bandit_pass/bandit14` → once logged in, prints the password file for the current level (readable only by that user)

## Sample Output
```bash
bandit13@bandit:~$ ls
sshkey.private

bandit13@bandit:~$ chmod 600 sshkey.private

bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost -p 2220
The authenticity of host '[localhost]:2220' can't be established.
Are you sure you want to continue connecting (yes/no)? yes
...
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- SSH supports **key-based authentication** as an alternative to passwords, using a public/private key pair.
- The `-i` flag tells `ssh` exactly which private key file to use for the connection.
- Passwords for each Bandit level are stored in `/etc/bandit_pass/<username>`, readable only by that specific user.

## Issue I Faced
Had to make sure the private key file had the correct (restrictive) permissions — SSH refuses to use a key file that's too open/world-readable, showing a "permissions too open" warning.

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
