# Bandit Level 0 → 1

**Goal:** Log in via SSH and read a password stored in a file, to get the password for the next level.

## Commands used

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
ls
cat readme
```

## Explanation

- `ssh` connects securely to the remote Bandit server using the given username and port.
- `ls` lists the files in the current directory — this revealed a file called `readme`.
- `cat readme` printed the contents of that file directly to the terminal, which contained the password for Level 1.

## Concept

This level is about the absolute basics: connecting to a remote Linux machine and reading a plain file. `ls` and `cat` are two of the most-used commands in Linux — you'll use them constantly, from CTFs to real system administration.

 [Watch the full walkthrough](https://youtube.com/@rootreport-056)
