# Bandit Level 2 → 3

## Goal
Read the contents of a file whose name contains spaces: `spaces in this filename`.

## Commands Used
```bash
cat "spaces in this filename"
```

## Command Explanation
- `cat "spaces in this filename"` → prints the contents of the file; quotes keep the whole name as **one** argument instead of the shell splitting it by spaces

## Sample Output
```bash
bandit2@bandit:~$ ls
spaces in this filename

bandit2@bandit:~$ cat spaces in this filename
cat: spaces: No such file or directory
cat: in: No such file or directory
cat: this: No such file or directory
cat: filename: No such file or directory

bandit2@bandit:~$ cat "spaces in this filename"
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- Filenames containing spaces can't be passed to commands as-is — the shell treats each space-separated word as a separate argument.
- To handle this, wrap the filename in **quotes** (`"..."`), or **escape** each space with a backslash (`\ `).

## Issue I Faced
Running `cat spaces in this filename` (without quotes) failed because the shell split it into multiple arguments instead of one filename.

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
