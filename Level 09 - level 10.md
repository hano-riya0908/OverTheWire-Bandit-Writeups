# Bandit Level 9 → 10

## Goal
The file `data.txt` contains mostly non-readable (binary) data. Find the human-readable password, which is preceded by several `=` characters.

## Commands Used
```bash
strings data.txt | grep '='
```

## Command Explanation
- `strings data.txt` → extracts only the printable/readable text sequences from a file that otherwise contains binary/garbage data
- `grep '='` → filters those readable strings down to lines containing the `=` character (since the password is preceded by `=` signs)

## Sample Output
```bash
bandit9@bandit:~$ strings data.txt | grep '='
========== xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- `strings` is great for pulling readable text out of binary files, executables, or corrupted-looking data.
- Combining `strings` with `grep` narrows down huge irrelevant output to just what's needed.

## Issue I Faced
Directly running `cat data.txt` printed a screen full of unreadable garbage characters — had to switch to `strings` to filter out the binary noise.

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
