# Bandit Level 2 → 3

**Goal:** Read a file whose name contains spaces, which normally breaks a simple `cat` command.

## Commands used

```bash
ls -la
cat "spaces in this filename"
```

## Explanation

- `ls -la` lists all files with full details, revealing a file named `spaces in this filename`.
- Running `cat spaces in this filename` without quotes fails, because the shell splits the command at each space and treats each word as a separate argument — so it looks for four different files instead of one.
- Wrapping the filename in double quotes (`"spaces in this filename"`) tells the shell to treat the whole thing as a single argument, spaces included.

## Concept

Same underlying idea as the Level 1→2 dash-filename trick, just a different symptom: the shell's word-splitting behavior can break commands if filenames aren't handled carefully. Quoting (or escaping spaces with a backslash, e.g. `spaces\ in\ this\ filename`) is the standard fix, and it's a habit that matters in real scripting too — unquoted variables are a classic source of bugs in shell scripts.

🎥 [Watch the full walkthrough](https://youtube.com/@rootreport-056)
