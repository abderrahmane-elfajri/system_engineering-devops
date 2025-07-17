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

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on shell variables, expansions, and aliases.
