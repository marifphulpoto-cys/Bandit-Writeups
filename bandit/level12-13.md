# Bandit Level 12 → Level 13

## Level Goal
The password for the next level is stored in the file `data.txt`, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under `/tmp` in which you can work.

## Commands you may need
`mkdir`, `cp`, `xxd`, `file`, `gzip`, `bzip2`, `tar`

## Connect to Level 12

```bash
ssh bandit12@bandit.labs.overthewire.org -p 2220
```

Password: (password obtained from level 11)

## Solution

### Step 1 — Set up a scratch workspace
Since we'll be creating multiple intermediate files, work in `/tmp` instead of the home directory:

```bash
mkdir /tmp/mywork12
cp ~/data.txt /tmp/mywork12/
cd /tmp/mywork12
```

### Step 2 — Reverse the hexdump
`data.txt` is a hex dump (created by a tool like `xxd`), not the raw binary. Convert it back to binary form using `xxd -r` (reverse mode):

```bash
xxd -r data.txt > data.bin
```

### Step 3 — Identify and decompress, repeatedly
Check what type of file you actually have:

```bash
file data.bin
```

This will report something like `gzip compressed data`. Depending on what it reports, decompress accordingly. You'll likely need to repeat this identify-then-decompress cycle several times, since the file was compressed multiple times in a row (e.g. gzip → bzip2 → gzip → tar → ...).

A typical repeating pattern looks like this:

```bash
mv data.bin data.gz
gzip -d data.gz
file data          # check the new type, e.g. "bzip2 compressed data"

mv data data.bz2
bzip2 -d data.bz2
file data          # check again, e.g. "POSIX tar archive"

tar -xf data
ls                 # see the extracted file, check its type again with `file`
```

Keep renaming the output to match the extension the correct tool expects (`.gz` for gzip, `.bz2` for bzip2, `.tar` for tar archives, etc.), running `file` after every step, and repeating until `file` reports something like `ASCII text`.

### Step 4 — Read the password
Once `file` reports plain ASCII text, view it:

```bash
cat <final_filename>
```

That's your password for Bandit Level 13.

## Key Concept
This level teaches you to never trust a file's extension — always verify the actual file type with the `file` command, which inspects the file's magic bytes/signature rather than its name. Compression tools can be chained (compressing an already-compressed file), so unwrapping a mystery file is often an iterative loop: identify → decompress/extract → identify again → repeat, until you reach the real content.

## Login to Level 13

```bash
ssh bandit13@bandit.labs.overthewire.org -p 2220
```
