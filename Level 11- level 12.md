# Bandit Level 11 → 12

## Goal
The file `data.txt` has all lowercase and uppercase letters **rotated by 13 positions** (ROT13 cipher). Decode it.

## Commands Used
```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

## Command Explanation
- `cat data.txt` → prints the raw ROT13-encoded content
- `tr 'A-Za-z' 'N-ZA-Mn-za-m'` → **translates/substitutes** each letter by shifting it 13 places in the alphabet (both cases), which reverses the ROT13 encoding
- `|` → feeds the raw text from `cat` into `tr` for character substitution

## Sample Output
```bash
bandit11@bandit:~$ cat data.txt
Gur cnffjbeq vf khhhhhhhhhhhhhhhhhhhhhhhhhhhhhhh

bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- ROT13 is a simple letter-substitution cipher where each letter is replaced by the one 13 positions after it in the alphabet — applying it twice returns the original text.
- `tr` is a handy command-line tool for character-by-character translation/substitution.

## Issue I Faced
The encoded text still looked like "real words" with a pattern, which was the clue it was a simple substitution cipher (ROT13) rather than full encryption.

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
