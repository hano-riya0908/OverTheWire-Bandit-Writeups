# Bandit Level 15 → 16

## Goal
Submit the current level's password to **port 30001 on localhost**, this time using **SSL/TLS encryption** to connect.

## Commands Used
```bash
cat /etc/bandit_pass/bandit15
nc localhost 30001
openssl s_client -connect localhost:30001
cat /etc/bandit_pass/bandit15 | openssl s_client -connect localhost:30001 -ign_eof
```

## Command Explanation
- `cat /etc/bandit_pass/bandit15` → reads/prints the current level's password
- `nc localhost 30001` → tried plain Netcat first, but this port expects an **encrypted** connection, so it fails/hangs
- `openssl s_client -connect localhost:30001` → opens an **SSL/TLS encrypted** connection to the port, required since this level uses encryption instead of plain text
- `-ign_eof` → tells `openssl` to keep the connection open after input ends (so it can still receive the server's response instead of closing immediately)
- `|` → pipes the password directly into the encrypted connection

## Sample Output
```bash
bandit15@bandit:~$ nc localhost 30001
(fails or hangs — port expects SSL, not plain text)

bandit15@bandit:~$ cat /etc/bandit_pass/bandit15 | openssl s_client -connect localhost:30001 -ign_eof
CONNECTED(00000003)
depth=0 ...
...
Correct!
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- Not all network services use plain text — some require an **SSL/TLS-encrypted** connection, which plain `nc` cannot handle.
- `openssl s_client` acts like Netcat but wraps the connection in SSL/TLS, useful for testing encrypted services manually.
- The `-ign_eof` flag is important here — without it, the connection closes right after sending input, before the server's reply can be read.

## Issue I Faced
Using plain `nc` on this port didn't work at all (no response) — took a bit to realize the port required SSL encryption, which is why `openssl s_client` was needed instead.

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
