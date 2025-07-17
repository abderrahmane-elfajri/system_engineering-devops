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

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on shell I/O redirections and filters.
