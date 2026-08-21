# Bandit Level 13 → Level 14

## Level Goal
The password for the next level is stored in `/etc/bandit_pass/bandit14` and can only be read by user `bandit14`. For this level, you don't get the next password, but you get a private SSH key that can be used to log into the next level.

## Commands you may need
`ssh`, `chmod`, `cat`

## Connect to Level 13

```bash
ssh bandit13@bandit.labs.overthewire.org -p 2220
```

Password: (password obtained from level 12)

## Solution

### Step 1 — Find the private key
List the files in the home directory:

```bash
ls -la
```

You'll see a file called `sshkey.private` — this is a private SSH key that lets you log in directly as `bandit14`, without needing a password.

### Step 2 — Use the key to SSH into bandit14
Use the `-i` flag to tell `ssh` which private key file to use for authentication:

```bash
ssh -i sshkey.private bandit14@localhost
```

Notice we're connecting to `localhost` — all Bandit levels actually live on the same machine, just as different Linux users, so once you're inside the Bandit environment, moving between levels via SSH keys means connecting back to `localhost` (default port 22) rather than the outward-facing `bandit.labs.overthewire.org -p 2220` address.

If SSH refuses the key due to file permissions (e.g. "UNPROTECTED PRIVATE KEY FILE" warning), fix the permissions first:

```bash
chmod 600 sshkey.private
```

Then retry the `ssh -i` command above.

### Step 3 — Read the password
Once logged in as `bandit14`, read the password file directly:

```bash
cat /etc/bandit_pass/bandit14
```

That's your password for Bandit Level 14.

## Key Concept
This level introduces **key-based SSH authentication** instead of password-based login — a private key proves your identity cryptographically, which is why SSH is strict about the key file's permissions (it must not be readable by other users, or SSH will refuse to use it as a security precaution). It also reinforces that every Bandit level is really just a separate local user account on the same host, reachable via `localhost` once you're already inside.

## Login to Level 14

```bash
ssh bandit14@bandit.labs.overthewire.org -p 2220
```
