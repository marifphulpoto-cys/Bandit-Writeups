# Bandit Level 14 → Level 15

## Level Goal
The password for the next level can be retrieved by submitting the current password to `port 30000` on `localhost`.

## Commands you may need
`nc` (netcat), `cat`

## Connect to Level 14

```bash
ssh bandit14@bandit.labs.overthewire.org -p 2220
```

Password: (password obtained from level 13)

## Solution

### Step 1 — Get your current password
This level needs you to *submit* the Bandit14 password to a listening service, so first read it:

```bash
cat /etc/bandit_pass/bandit14
```

(You should already have this from completing Level 13, since bandit13's key logged you straight into bandit14.)

### Step 2 — Connect to the service on port 30000
Use `netcat` (`nc`) to open a raw connection to the local service listening on port 30000:

```bash
nc localhost 30000
```

### Step 3 — Submit the password
Once connected, the terminal will look like it's just sitting there — this is because you now have an open connection to the service. Simply type (or paste) the bandit14 password and press Enter:

```
<bandit14_password>
```

The service will respond with the password for Bandit Level 15, then close the connection.

### Alternative one-liner
Instead of connecting interactively, you can pipe the password directly into `nc`:

```bash
echo <bandit14_password> | nc localhost 30000
```

## Key Concept
This level introduces **netcat**, a versatile networking tool often called the "Swiss army knife" of TCP/IP — it can open raw connections to any host/port and send or receive data directly, without needing a purpose-built client. This is the foundation for later levels that move from plain-text services to encrypted ones (like SSL/TLS with `openssl s_client`).

## Login to Level 15

```bash
ssh bandit15@bandit.labs.overthewire.org -p 2220
```
