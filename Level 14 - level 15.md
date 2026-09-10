# Bandit Level 14 → 15

## Goal
Submit the current level's password to **port 30000 on localhost** to receive the password for the next level.

## Commands Used
```bash
cat /etc/bandit_pass/bandit14
nc localhost 30000
cat /etc/bandit_pass/bandit14 | nc localhost 30000
```

## Command Explanation
- `cat /etc/bandit_pass/bandit14` → reads/prints the current level's password from its file
- `nc localhost 30000` → **Netcat**, opens a raw, interactive network connection to `localhost` on port `30000` (tried manually first)
- `cat /etc/bandit_pass/bandit14 | nc localhost 30000` → pipes the password text directly into the connection as the input the listening service expects, avoiding manual typing

## Sample Output
```bash
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
<current password>

bandit14@bandit:~$ nc localhost 30000
(waits here — need to type/paste the password manually)

bandit14@bandit:~$ cat /etc/bandit_pass/bandit14 | nc localhost 30000
Correct!
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- `nc` (Netcat) is a versatile networking tool used to read/write data across network connections — often called the "Swiss army knife" of networking.
- Some services listen on specific ports expecting a certain input (here, the current password) before responding with data.

## Issue I Faced
Typing the password manually into an interactive `nc` session was error-prone — piping it directly with `cat | nc` was more reliable and repeatable.

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
