# Bandit Level 10 → 11

## Goal
The file `data.txt` contains the password encoded in **Base64**. Decode it.

## Commands Used
```bash
cat data.txt | base64 -d
```

## Command Explanation
- `cat data.txt` → prints the raw (Base64-encoded) content of the file
- `base64 -d` → decodes Base64-encoded input back into its original readable text (`-d` = decode)
- `|` → passes the encoded content from `cat` directly into `base64 -d` for decoding

## Sample Output
```bash
bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eA==

bandit10@bandit:~$ cat data.txt | base64 -d
The password is xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- Base64 is an encoding (not encryption) used to represent binary/text data in ASCII form — easily reversible.
- The `base64` command can both encode (default) and decode (`-d` flag) content.

## Issue I Faced
The raw file looked like random jumbled text at first — recognizing the `==` padding and character set helped identify it as Base64.

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
