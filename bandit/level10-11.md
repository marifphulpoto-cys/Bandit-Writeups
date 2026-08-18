# Bandit Level 10 → Level 11

## Level Goal
The password for the next level is stored in the file `data.txt`, which contains base64 encoded data.

## Commands you may need
`man base64`

## Connect to Level 10

```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
```

Password: (password obtained from level 9)

## Solution

1. List the files in the home directory:

```bash
ls -la
```

You'll see a file called `data.txt`.

2. View the contents of the file:

```bash
cat data.txt
```

The output will look like a random base64-encoded string, something like:

```
VGhlIHBhc3N3b3JkIGlzIGJ...
```

3. Decode the base64 string using the `base64` command with the `-d` (decode) flag:

```bash
base64 -d data.txt
```

This prints out a line of text such as:

```
The password is <password>
```

4. That password is your login for Bandit Level 11.

## Key Concept
Base64 is an **encoding** scheme, not encryption — it's fully reversible with no key required. It's commonly used to represent binary data in ASCII text form (e.g., in emails, URLs, config files). Recognizing base64 strings (they use A-Z, a-z, 0-9, `+`, `/`, and `=` padding at the end) is a useful skill, since decoding them is trivial once identified.

## Login to Level 11

```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
```
