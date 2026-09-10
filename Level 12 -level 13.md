# Bandit Level 12 → 13

## Goal
The file `data.txt` is a **hexdump of a file that has been repeatedly compressed** (multiple times, with different compression tools). Reverse it step by step to get the password.

## Commands Used
```bash
mkdir /tmp/work12
cp data.txt /tmp/work12/
cd /tmp/work12

xxd -r data.txt > data
file data

# repeat based on file type detected each time:
mv data data.gz
gunzip data.gz
file data

mv data data.bz2
bunzip2 data.bz2
file data

mv data data.tar
tar -xf data.tar
file <resulting_file>

# ...continue extracting until a plain ASCII text file is found
cat <final_file>
```

## Command Explanation
- `mkdir /tmp/work12` → creates a temporary working folder (safer than working directly in home directory)
- `cp data.txt /tmp/work12/` → copies the file to the working folder
- `xxd -r data.txt > data` → reverses a hexdump back into its original binary form (`-r` = reverse mode)
- `file data` → identifies the actual compression/file type at each stage (gzip, bzip2, tar, etc.)
- `mv data data.gz` (etc.) → renames the file with the correct extension so the matching decompression tool works properly
- `gunzip` / `bunzip2` / `tar -xf` → decompress/extract based on whichever compression type `file` reports
- `cat <final_file>` → once a plain ASCII text file is reached, prints the password

## Sample Output
```bash
bandit12@bandit:~$ xxd -r data.txt > data
bandit12@bandit:~$ file data
data: gzip compressed data

bandit12@bandit:~$ mv data data.gz && gunzip data.gz
bandit12@bandit:~$ file data
data: bzip2 compressed data

... (repeats through several compression layers: gzip, bzip2, tar, etc.)

bandit12@bandit:~$ file data8
data8: ASCII text

bandit12@bandit:~$ cat data8
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- A hexdump can be reversed back to raw binary using `xxd -r`.
- The `file` command is essential here — it tells you which compression format you're dealing with at each layer, since the extension alone means nothing until renamed.
- Files can be compressed multiple times in a row (nested), requiring repeated identify → rename → extract cycles.

## Issue I Faced
Each decompression step revealed *another* compressed file in a different format — lost track of how many layers deep I was a couple of times, so working in a clean temp folder helped avoid confusion with leftover files.

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
