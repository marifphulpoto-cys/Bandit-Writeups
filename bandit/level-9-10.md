Level 9 → Level 10
Goal

The password for the next level is stored in the file data.txt, which contains mostly binary/non-printable data, but the password itself is a human-readable string preceded by several = characters.

Concept

Two tools come into play here:

strings — scans a binary/mixed file and pulls out sequences of printable characters (by default, runs of 4+ printable characters). This is the standard way to fish readable text out of a file that isn't plain text.
grep — filters that output down to lines matching a pattern. Since we're told the password is preceded by = characters, we search for lines containing =.
Command
bash
strings data.txt | grep '='

If that still returns multiple candidate lines, narrow it further — the real password line typically has several consecutive = signs right before it, so you can tighten the pattern:

bash
strings data.txt | grep '==='
Why this works

strings avoids you having to manually eyeball a file full of unreadable binary junk — it does the filtering for "is this actually text" for you. grep '=' then narrows a large strings output down to the one or two lines matching the clue given in the level description, instead of scrolling through everything by hand.
