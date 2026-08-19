# Bandit Level 11 → Level 12

## Level Goal
The password for the next level is stored in the file `data.txt`, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions (ROT13 cipher).

## Commands you may need
`man tr`

## Connect to Level 11

```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
```

Password: (password obtained from level 10)

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

The output will look like scrambled text, something like:

```
Gur cnffjbeq vf <fbzrguvat>
```

3. This is ROT13-encoded text — every letter is shifted 13 places in the alphabet. Since the alphabet has 26 letters, applying ROT13 twice returns the original text, which makes it self-inverse (encoding and decoding use the exact same operation).

Decode it using the `tr` (translate) command, mapping each letter to the one 13 positions ahead:

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

This prints out the decoded line, such as:

```
The password is <password>
```

4. That password is your login for Bandit Level 12.

## Key Concept
ROT13 is a simple substitution cipher, not real encryption — it provides no security, only obfuscation (historically used to hide spoilers or answers from casual reading). The `tr` command works by mapping each character in the first set to the corresponding character in the second set — here, `A-Za-z` maps each letter to the one 13 positions later in the alphabet (wrapping around), which is exactly how ROT13 shifts work.

## Login to Level 12

```bash
ssh bandit12@bandit.labs.overthewire.org -p 2220
```
