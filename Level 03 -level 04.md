# Bandit Level 3 → 4

## Goal
Find a password stored in a **hidden file** inside the `inhere` directory.

## Commands Used
```bash
cd inhere
ls -la
cat .hidden
```

## Command Explanation
- `cd inhere` → moves into the `inhere` directory
- `ls -la` → lists **all** files including hidden ones (`-a`), with detailed info like permissions and size (`-l`)
- `cat .hidden` → prints the contents of the hidden file `.hidden`

## Sample Output
```bash
bandit3@bandit:~$ cd inhere

bandit3@bandit:~/inhere$ ls
(empty output)

bandit3@bandit:~/inhere$ ls -la
total 12
drwxr-xr-x  2 root     root     4096 ...  .
drwxr-xr-x 21 root     root     4096 ...  ..
-rw-r-----  1 bandit4  bandit3    33 ...  .hidden

bandit3@bandit:~/inhere$ cat .hidden
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- Files/directories starting with a `.` are **hidden** in Linux and don't show up with a plain `ls`.
- The `-a` flag (all) with `ls` reveals hidden files; `-l` gives a detailed listing (permissions, size, owner, etc.).

## Issue I Faced
A normal `ls` inside `inhere` showed nothing useful — the file was hidden, so I had to remember to use `ls -la` to reveal it.

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
