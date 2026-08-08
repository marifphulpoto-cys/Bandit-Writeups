# Bandit Level 3 → 4

**Goal:** Find and read a hidden file inside a directory called `inhere`.

## Commands used

```bash
cd inhere
ls -la
cat .hidden
```

## Explanation

- `cd inhere` moves into the target directory for this level.
- A normal `ls` here shows nothing — the file is hidden. In Linux, any file starting with a dot (`.`) is treated as hidden and won't appear in a standard listing.
- `ls -la` fixes this: the `-a` flag shows all files, including hidden ones, and `-l` gives the detailed listing. This reveals a file named `.hidden`.
- `cat .hidden` reads the file directly, printing the password for the next level.

## Concept

Hidden files aren't a security feature — they're just a display convention. Real systems use dotfiles constantly for configuration (`.bashrc`, `.ssh/`, `.gitignore`, etc.), so knowing to check for them with `ls -la` is a basic but essential habit. Never assume a directory is empty just because a plain `ls` shows nothing.

🎥 [Watch the full walkthrough](https://youtube.com/@rootreport-056)
