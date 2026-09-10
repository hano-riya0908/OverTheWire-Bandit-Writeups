# Bandit Level 1 → 2

## Goal
Read the contents of a file called `-` (a single dash) located in the home directory.

## Commands Used
```bash
cat ./-
```

## Command Explanation
- `cat ./-` → prints the contents of a file literally named `-`; the `./` prefix stops the shell from treating `-` as a special stdin/flag reference

## Sample Output
```bash
bandit1@bandit:~$ ls
-

bandit1@bandit:~$ cat -
(terminal just hangs, waiting for keyboard input — nothing prints)

bandit1@bandit:~$ cat ./-
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## What I Learned
- A filename of just `-` has special meaning to many commands — it's often interpreted as **stdin/stdout**, not a literal file.
- Running `cat -` doesn't work as expected because the shell/command treats `-` as a flag or stream reference.
- Prefixing the filename with `./` tells the shell "look for a file named `-` in the current directory" instead of interpreting it specially.

## Issue I Faced
`cat -` didn't work — it just waited for input instead of printing the file, since `-` was being interpreted as stdin.

## Password
```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
*(masked intentionally — try solving it yourself!)*
