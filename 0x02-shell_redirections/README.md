# 0x02. Shell, I/O Redirections and filters

This directory contains scripts that demonstrate shell I/O redirections and filters.

## Files

### 0-hello_world
A script that prints "Hello, World", followed by a new line to the standard output.

**Usage:**
```bash
chmod +x ./0-hello_world
./0-hello_world
```

**Expected output:**
```
Hello, World
```

**Command used:** `echo "Hello, World"`

**Expected behavior:**
- Prints "Hello, World" to standard output
- Followed by a new line
- Uses the `echo` command to output text
- The output can be piped to other commands like `cat -e` to show line endings

**Verification:**
```bash
./0-hello_world | cat -e
# Should show: Hello, World$
```

### 1-confused_smiley
A script that displays a confused smiley "(Ôo)'.

**Usage:**
```bash
chmod +x ./1-confused_smiley
./1-confused_smiley
```

**Expected output:**
```
"(Ôo)'
```

**Command used:** `echo "\"(Ôo)'"`

**Expected behavior:**
- Prints the confused smiley `"(Ôo)'` to standard output
- Uses the `echo` command to output the text
- The double quote at the beginning is escaped with `\"`
- The single quote at the end is included as-is
- The special character `Ô` is included in the output

### 2-hellofile
A script that displays the content of the `/etc/passwd` file.

**Usage:**
```bash
chmod +x ./2-hellofile
./2-hellofile
```

**Expected output:**
```
##
# User Database
#
# Note that this file is consulted directly only when the system is running
# in single-user mode. At other times this information is provided by
# Open Directory.
#
# See the opendirectoryd(8) man page for additional information about
# Open Directory.
##
nobody:*:-2:-2:Unprivileged User:/var/empty:/usr/bin/false
root:*:0:0:System Administrator:/var/root:/bin/sh
daemon:*:1:1:System Services:/var/root:/usr/bin/false
_uucp:*:4:4:Unix to Unix Copy Protocol:/var/spool/uucp:/usr/sbin/uucico
_taskgated:*:13:13:Task Gate Daemon:/var/empty:/usr/bin/false
_networkd:*:24:24:Network Services:/var/networkd:/usr/bin/false
_installassistant:*:25:25:Install Assistant:/var/empty:/usr/bin/false
_lp:*:26:26:Printing Services:/var/spool/cups:/usr/bin/false
_postfix:*:27:27:Postfix Mail Server:/var/spool/postfix:/usr/bin/false
_scsd:*:31:31:Service Configuration Service:/var/empty:/usr/bin/false
_ces:*:32:32:Certificate Enrollment Service:/var/empty:/usr/bin/false
_mcxalr:*:54:54:MCX AppLaunch:/var/empty:/usr/bin/false
_krbfast:*:246:-2:Kerberos FAST Account:/var/empty:/usr/bin/false
```

**Command used:** `cat /etc/passwd`

**Expected behavior:**
- Displays the entire content of the `/etc/passwd` file
- Uses the `cat` command to read and output file contents
- The `/etc/passwd` file contains user account information
- Each line represents a user account with fields separated by colons
- The output will vary depending on the system's user accounts

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on shell I/O redirections and filters.
