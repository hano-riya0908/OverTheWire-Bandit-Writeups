# Bandit Level 8 → 9

## Goal
Find the **only line that occurs once** in the file `data.txt` (every other line is repeated).

## Commands Used
```bash
sort data.txt | uniq -u
```

## Command Explanation
- `sort data.txt` → sorts all lines in the file alphabetically (required before `uniq` can detect duplicates properly)
- `uniq -u` → from the sorted input, prints only the lines that are **unique** (appear exactly once)
- `|` (pipe) → sends the output of `sort` directly as input into `uniq`

## Sample Output
```bash
bandit8@bandit:~$ sort data.txt | uniq -u
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- `uniq` only detects duplicate lines that are **adjacent**, which is why sorting first is necessary.
- Piping (`|`) lets you chain multiple commands so the output of one becomes the input of the next.

## Issue I Faced
Running `uniq -u` directly on the unsorted file gave wrong/no results — had to remember that `sort` must come first for `uniq` to work correctly.

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
