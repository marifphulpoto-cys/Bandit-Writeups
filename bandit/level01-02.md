# Bandit Level 1 → 2

**Goal:** Read a file whose name is just a single dash (`-`), which normally gets misread as a command flag instead of a filename.

## Commands used

```bash
ls -la
cat ./-
```

## Explanation

- `ls -la` lists all files, including hidden ones, with full details — this revealed a file literally named `-`.
- Running `cat -` directly doesn't work as expected, because `-` is often interpreted as an option/flag by many commands (or as a signal to read from standard input), not as a filename.
- Using `cat ./-` fixes this by specifying the file's path explicitly. The `./` tells the shell "this is a file in the current directory," so the `-` is treated purely as part of the filename, not as a flag.

## Concept

This is a classic Linux gotcha: filenames starting with `-` can break commands if you're not careful. Prefixing with `./` (or using `--` before the filename in supporting commands) is the standard fix, and it's a habit worth having for real-world Linux work, not just this wargame.

 [Watch the full walkthrough](https://youtube.com/@rootreport-056)
