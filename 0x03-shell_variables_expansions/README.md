# 0x03. Shell, init files, variables and expansions

This directory contains scripts that demonstrate shell variables, expansions, and aliases.

## Files

### 0-alias
A script that creates an alias where `ls` command becomes `rm *`.

**Usage:**
```bash
source ./0-alias
```

**Expected behavior:**
- Creates an alias that makes `ls` execute `rm *` instead
- Must be sourced (not executed) to affect the current shell
- After sourcing, typing `ls` will delete all files in the current directory
- Use `\ls` to bypass the alias and use the original `ls` command

**Example:**
```bash
julien@ubuntu:/tmp/0x03$ ls
0-alias  file1  file2
julien@ubuntu:/tmp/0x03$ source ./0-alias 
julien@ubuntu:/tmp/0x03$ ls
julien@ubuntu:/tmp/0x03$ \ls
julien@ubuntu:/tmp/0x03$ 
```

**Command used:** `alias ls="rm *"`

**Warning:** This alias is dangerous as it replaces the `ls` command with file deletion. Use with caution.

### 1-hello_you
A script that prints "hello user", where user is the current Linux user.

**Usage:**
```bash
chmod +x ./1-hello_you
./1-hello_you
```

**Expected output:**
```
hello julien
```
(where "julien" is replaced with the actual current user)

**Example:**
```bash
julien@ubuntu:/tmp/0x03$ id
uid=1000(julien) gid=1000(julien) groups=1000(julien),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),113(lpadmin),128(sambashare)
julien@ubuntu:/tmp/0x03$ chmod +x ./1-hello_you 
julien@ubuntu:/tmp/0x03$ ./1-hello_you 
hello julien
```

**Command used:** `echo "hello $USER"`

**Expected behavior:**
- Uses the `$USER` environment variable to get the current user's name
- Prints a greeting message with the current user's name
- The `$USER` variable contains the username of the currently logged-in user
- Works for any user who executes the script
- Demonstrates shell variable expansion

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on shell variables, expansions, and aliases.
