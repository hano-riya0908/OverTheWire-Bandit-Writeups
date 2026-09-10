# Bandit Level 5 → 6

## Goal
Find a file inside the `inhere` directory tree that matches **all** of these conditions:
- human-readable
- exactly **1033 bytes** in size
- **not executable**

## Commands Used
```bash
find inhere -type f -size 1033c ! -executable
cat <filename>
```

## Command Explanation
- `find inhere -type f -size 1033c ! -executable` → searches recursively inside `inhere` for a **regular file** (`-type f`) that is **exactly 1033 bytes** (`-size 1033c`) and **not executable** (`! -executable`)
- `cat <filename>` → prints the contents of the matched file

## Sample Output
```bash
bandit5@bandit:~$ find inhere -type f -size 1033c ! -executable
inhere/maybehere07/.file2

bandit5@bandit:~$ cat inhere/maybehere07/.file2
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- `find` can search recursively and filter by multiple conditions at once.
- Flags used:
  - `-type f` → only regular files
  - `-size 1033c` → exactly 1033 bytes (the `c` suffix means bytes)
  - `! -executable` → exclude executable files
- Combining conditions in `find` narrows down results fast, even in deeply nested directories.

## Issue I Faced
There were many nested subdirectories and files with similar names, so figuring out the right combination of `find` options took some trial and error before I got the exact match.

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
