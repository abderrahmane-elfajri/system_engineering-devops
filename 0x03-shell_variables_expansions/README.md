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

### 2-path
A script that adds `/action` to the PATH environment variable, ensuring that `/action` is the last directory the shell looks into when searching for programs.

**Usage:**
```bash
source ./2-path
```

**Expected behavior:**
- Appends `/action` to the end of the current PATH
- Must be sourced (not executed) to affect the current shell environment
- The `/action` directory becomes the last directory searched for executables

**Example:**
```bash
julien@ubuntu:/tmp/0x03$ echo $PATH
/home/julien/bin:/home/julien/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

julien@ubuntu:/tmp/0x03$ source ./2-path 

julien@ubuntu:/tmp/0x03$ echo $PATH
/home/julien/bin:/home/julien/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/action
```

**Command used:** `export PATH="$PATH:/action"`

**Expected behavior:**
- Uses `export` to make the PATH variable available to child processes
- `$PATH` expands to the current PATH value
- `:` is the delimiter between directories in PATH
- `/action` is appended as the last directory
- The shell will search `/action` last when looking for executables
- Demonstrates PATH manipulation and environment variable modification

### 3-paths
A script that counts the number of directories in the PATH environment variable.

**Usage:**
```bash
chmod +x ./3-paths
./3-paths
```
or
```bash
. ./3-paths
```

**Expected output:**
```
11
```
(The actual number depends on your PATH configuration)

**Example:**
```bash
julien@ubuntu:/tmp/0x03$ echo $PATH
/home/julien/bin:/home/julien/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

julien@ubuntu:/tmp/0x03$ . ./3-paths 
11

julien@ubuntu:/tmp/0x03$ PATH=/home/julien/bin:/home/julien/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:::::/hello

julien@ubuntu:/tmp/0x03$ . ./3-paths 
12
```

**Command used:** `echo $PATH | tr ':' '\n' | wc -l`

**Expected behavior:**
- `echo $PATH` outputs the PATH environment variable
- `tr ':' '\n'` replaces each colon with a newline, putting each directory on its own line
- `wc -l` counts the number of lines, which equals the number of directories
- Handles empty directories (consecutive colons) correctly by counting them as separate entries
- Works with any PATH configuration
- Demonstrates string manipulation and pipe operations

**How it works:**
1. PATH directories are separated by colons `:`
2. `tr` (translate) replaces colons with newlines
3. `wc -l` counts the resulting lines
4. Each line represents one directory in the PATH

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on shell variables, expansions, and aliases.
