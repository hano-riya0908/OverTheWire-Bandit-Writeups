# Bandit Level 4 → 5

## Goal
Among several files in the `inhere` directory, find the one that is **human-readable** and read the password from it.

## Commands Used
```bash
cd inhere
file ./*
cat ./-file07
```

## Command Explanation
- `cd inhere` → moves into the `inhere` directory
- `file ./*` → checks the actual **type/content** of every file in the folder (text, data, binary, etc.), regardless of its name
- `cat ./-file07` → prints the contents of the identified human-readable file

## Sample Output
```bash
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data

bandit4@bandit:~/inhere$ cat ./-file07
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- The `file` command inspects file content and tells you its actual type (e.g. ASCII text, data, executable) — regardless of the filename.
- This is useful when filenames are misleading or non-descriptive (e.g. `-file00`, `-file01`, ...).

## Issue I Faced
With multiple similarly-named files, it was confusing to figure out which one actually contained readable text until I ran `file` on all of them at once.

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
