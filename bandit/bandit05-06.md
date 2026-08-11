# Bandit Level 5 → 6

**Goal:** Find one specific file, out of many nested inside subdirectories, that matches three exact properties: human-readable, 1033 bytes in size, and not executable.

## Commands used

```bash
find -size 1033c -readable ! -executable
cat <resulting file>
```

## Explanation

- The `inhere` directory for this level contains many subdirectories, each with several decoy files — too many to check manually.
- `find` searches recursively by default, checking every file in every subdirectory from the current location.
- `-size 1033c` matches files that are exactly 1033 bytes (the `c` suffix means bytes, not blocks).
- `-readable` matches files the current user has permission to read.
- `! -executable` excludes files marked as executable — the `!` negates the condition.
- Combining all three filters narrows a large, nested pile of files down to exactly one match, which is then read with `cat`.

## Concept

This is the same `find`-filtering technique from Level 4→5, but applied recursively across nested folders instead of a single flat directory — a more realistic version of the same real-world skill: isolating one specific file out of a large, messy filesystem using its properties rather than guessing by name or location.

🎥 [Watch the full walkthrough](https://youtube.com/@rootreport-056)
