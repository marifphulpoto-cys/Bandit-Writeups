# Bandit Level 4 → 5

**Goal:** Find and read the one human-readable file among several files in a directory, then read the password from a file matching specific properties (size and permissions).

## Commands used

```bash
cd inhere
find . -size 1033c -readable ! -executable
cat <resulting file>
```

## Explanation

- `cd inhere` moves into the directory containing multiple candidate files, most of which are decoys.
- `find . -size 1033c -readable ! -executable` searches the current directory for a file that matches three conditions at once:
  - `-size 1033c` — exactly 1033 bytes in size
  - `-readable` — the current user has permission to read it
  - `! -executable` — it is *not* marked as executable (the `!` negates the condition)
- Combining all three filters narrows a folder full of similar-looking files down to exactly one match.
- `cat` on the resulting filename prints the password.

## Concept

`find` is one of the most powerful tools in Linux for locating files based on properties rather than names — size, permissions, ownership, modification time, and more can all be combined in a single command. This is a genuinely practical real-world skill: narrowing down "the one file that matters" out of hundreds or thousands is something you'll do constantly in system administration, forensics, and security work.

🎥 [Watch the full walkthrough](https://youtube.com/@rootreport-056)
