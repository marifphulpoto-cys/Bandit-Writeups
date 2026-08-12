# Bandit Level 6 → 7

**Goal:** Find a file located somewhere on the entire filesystem, owned by a specific user and group, with an exact size, while suppressing the "permission denied" noise from searching folders you can't access.

## Commands used

```bash
find / -user bandit7 -group bandit7 -size 33c 2>/dev/null
cat <resulting file>
```

## Explanation

- `find /` starts the search from the root of the entire filesystem, not just the current directory — this level's file could be anywhere.
- `-user bandit7` filters for files owned by the user `bandit7`.
- `-group bandit7` filters further, matching only files that also belong to the `bandit7` group.
- `-size 33c` adds a third filter: the file must be exactly 33 bytes.
- `2>/dev/null` redirects error output (stderr) to `/dev/null`, silently discarding it — this hides the large number of "Permission denied" messages that come from `find` trying to search directories the current user isn't allowed to read.
- The remaining output is the one file matching all three conditions, which is then read with `cat`.

## Concept

Searching from `/` (the filesystem root) is powerful but noisy — most systems have plenty of directories a regular user can't access, and `find` will report every one of them as an error unless that output is suppressed. Redirecting stderr with `2>/dev/null` is a common, practical habit in real Linux work: separating the results you actually want from the errors cluttering the output.

🎥 [Watch the full walkthrough](https://youtube.com/@rootreport-056)
