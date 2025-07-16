# 0x01. Shell, permissions

This directory contains scripts that demonstrate shell permissions and user management operations.

## Files

### 0-iam_betty
A script that switches the current user to the user betty.

**Usage:**
```bash
chmod +x ./0-iam_betty
./0-iam_betty
```

**Command used:** `su betty` (exactly 8 characters)

**Expected behavior:**
- Switches to user betty
- Assumes user betty exists on the system
- Uses the `su` (switch user) command

**Character count verification:**
```bash
tail -1 0-iam_betty | wc -c
# Should return 9 (8 characters + newline)
```

The script uses the `su` command which stands for "switch user" and allows switching to another user account.

### 1-who_am_i
A script that prints the effective username of the current user.

**Usage:**
```bash
chmod +x ./1-who_am_i
./1-who_am_i
```

**Expected output:**
```
julien
```

**Command used:** `whoami`

**Expected behavior:**
- Prints the effective username of the current user
- Works with any user account
- Uses the `whoami` command to get the current user

The script uses the `whoami` command which displays the username of the current effective user.

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on shell permissions and user management fundamentals.
