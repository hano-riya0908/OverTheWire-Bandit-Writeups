# Bandit Level 7 → 8

## Goal
Find the password in the file `data.txt`, located next to the word `millionth`.

## Commands Used
```bash
grep millionth data.txt
```

## Command Explanation
- `grep millionth data.txt` → searches the file `data.txt` for lines containing the word `millionth`, and prints only those matching lines

## Sample Output
```bash
bandit7@bandit:~$ grep millionth data.txt
millionth    xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- `grep` is a powerful text-search tool that scans files line by line for a given pattern/keyword.
- Useful when a huge file has one relevant line hidden among thousands of others.

## Issue I Faced
`data.txt` had a huge number of lines, so scrolling manually to find the right one wasn't practical — `grep` solved that instantly.

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
