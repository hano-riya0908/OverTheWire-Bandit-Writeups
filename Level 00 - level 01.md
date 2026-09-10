# Bandit Level 0 → 1

## Goal
Connect to the Bandit game server via SSH and find the password for the next level.

## Commands Used
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
pwd
ls
cat readme
```

## Command Explanation
- `ssh bandit0@bandit.labs.overthewire.org -p 2220` → connects to the remote server as user `bandit0` on port `2220`
- `pwd` → prints the current working directory, to confirm where I landed after login
- `ls` → lists files in the current directory
- `cat readme` → prints the contents of the file `readme` to the screen

## Sample Output
```bash
$ ssh bandit0@bandit.labs.overthewire.org -p 2220
bandit0@bandit.labs.overthewire.org's password:
Welcome to OverTheWire!
...
bandit0@bandit:~$ pwd
/home/bandit0

bandit0@bandit:~$ ls
readme

bandit0@bandit:~$ cat readme
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- How to connect to a remote server using **SSH**, specifying the username, host, and port.
- Basic Linux navigation commands: `ls` to list files, `cat` to read file contents.
- The password for the next level was stored in a file called `readme` in the home directory.

## Issue I Faced
Kept getting **permission denied** — the SSH password prompt failed multiple times (30+ attempts) before I got the input right. Turned out I needed to be more careful typing the password (special characters / copy-paste issues).

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
