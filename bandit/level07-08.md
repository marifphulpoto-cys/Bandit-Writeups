# Bandit Level 7 → Level 8

## Goal
The password for the next level is stored in the file `data.txt`, next to the word `millionth`.

## Connect
```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
```

## Explore
```bash
ls -la
```
You'll find a single file: `data.txt`. Check its size first:
```bash
wc -l data.txt
```
This shows it has a huge number of lines — way too many to scroll through manually. That's the whole point of this level: it teaches you to filter large files for a specific pattern instead of reading them by eye.

## The Command: `grep`
`grep` searches a file (or input stream) line by line for lines that match a pattern, and prints only those lines.

```bash
grep millionth data.txt
```

**How it works:**
- `grep` = the command
- `millionth` = the pattern (string) you're searching for
- `data.txt` = the file to search in

Since we know the password sits right next to the word "millionth" on the same line, grep pulls out exactly that line instead of you having to eyeball thousands of lines.

## Output
```
millionth       XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```
(The `X`s represent the actual password string — copy it as-is.)

## Key takeaway
`grep` is one of the most-used tools in a security/sysadmin workflow — you'll use it constantly for filtering logs, searching source code for secrets, or hunting for specific strings inside large text dumps. Useful variations to know:
- `grep -i` → case-insensitive search
- `grep -r` → recursive search through a directory
- `grep -n` → show line numbers of matches
- `grep -v` → show lines that do NOT match

## Login to Level 8
```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
```
