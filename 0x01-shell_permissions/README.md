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

### 2-groups
A script that prints all the groups the current user is part of.

**Usage:**
```bash
chmod +x ./2-groups
./2-groups
```

**Expected output:**
```
julien adm cdrom sudo dip plugdev lpadmin sambashare
```

**Command used:** `groups`

**Expected behavior:**
- Prints all groups the current user belongs to
- Output varies depending on the user and system configuration
- Uses the `groups` command to list user group memberships
- Shows both primary and supplementary groups

### 3-new_owner
A script that changes the owner of the file hello to the user betty.

**Usage:**
```bash
chmod +x ./3-new_owner
sudo ./3-new_owner
```

**Expected behavior:**
```bash
# Before running the script
julien@ubuntu:/tmp/h$ ls -l
total 4
-rwxrw-r-- 1 julien julien 30 Sep 20 14:23 3-new_owner
-rw-rw-r-- 1 julien julien  0 Sep 20 14:18 hello

# After running the script
julien@ubuntu:/tmp/h$ sudo ./3-new_owner 
julien@ubuntu:/tmp/h$ ls -l
total 4
-rwxrw-r-- 1 julien julien 30 Sep 20 14:23 3-new_owner
-rw-rw-r-- 1 betty  julien  0 Sep 20 14:18 hello
```

**Command used:** `chown betty hello`

**Expected behavior:**
- Changes the owner of the file "hello" to user "betty"
- Requires sudo privileges to change file ownership
- Uses the `chown` command (change owner)
- Assumes the file "hello" exists in the current directory
- Assumes user "betty" exists on the system

### 4-empty
A script that creates an empty file called hello.

**Usage:**
```bash
chmod +x ./4-empty
./4-empty
```

**Expected behavior:**
```bash
# Before running the script
julien@ubuntu:/tmp/h$ ls -l
total 4
-rwxrw-r-- 1 julien julien 30 Sep 20 14:23 4-empty

# After running the script
julien@ubuntu:/tmp/h$ ./4-empty
julien@ubuntu:/tmp/h$ ls -l
total 4
-rwxrw-r-- 1 julien julien 30 Sep 20 14:23 4-empty
-rw-rw-r-- 1 julien julien  0 Sep 20 14:25 hello
```

**Command used:** `touch hello`

**Expected behavior:**
- Creates an empty file named "hello"
- Uses the `touch` command to create the file
- If the file already exists, it updates the timestamp
- Creates the file with default permissions
- No output is produced when successful

### 5-execute
A script that adds execute permission to the owner of the file hello.

**Usage:**
```bash
chmod +x ./5-execute
./5-execute
```

**Expected behavior:**
```bash
# Before running the script
julien@ubuntu:/tmp/h$ ls -l
total 8
-rwxrw-r-- 1 julien julien 28 Sep 20 14:26 5-execute
-rw-rw-r-- 1 julien julien 23 Sep 20 14:25 hello
julien@ubuntu:/tmp/h$ ./hello
bash: ./hello: Permission denied

# After running the script
julien@ubuntu:/tmp/h$ ./5-execute 
julien@ubuntu:/tmp/h$ ls -l
total 8
-rwxrw-r-- 1 julien julien 28 Sep 20 14:26 5-execute
-rwxrw-r-- 1 julien julien 23 Sep 20 14:25 hello
```

**Command used:** `chmod u+x hello`

**Expected behavior:**
- Adds execute permission to the owner of the file "hello"
- Uses the `chmod` command (change mode/permissions)
- `u+x` means "add execute permission for the user (owner)"
- Assumes the file "hello" exists in the current directory
- After running, the owner can execute the file
- The file permissions change from `-rw-rw-r--` to `-rwxrw-r--`

### 8-James_Bond
A script that sets the permission to the file hello the same as olleh.

**Usage:**
```bash
chmod +x ./8-James_Bond
./8-James_Bond
```

**Expected behavior:**
- Sets the mode of the file "hello" to `-rwx--x--x` (octal 711)
- Uses the `chmod` command with octal notation
- The permissions are: owner (rwx), group (--x), others (--x)
- File must exist in the current directory
- After running, the file has permissions 711

**Command used:** `chmod 007 hello`

**Expected behavior:**
- Sets the mode of the file "hello" to `----rwx` (octal 007)
- Uses the `chmod` command with octal notation
- Only others have read, write, and execute permissions
- Owner and group have no permissions
- File must exist in the current directory

### 9-John_Doe
A script that sets the mode of the file hello to `-rwxr-x-wx`.

**Usage:**
```bash
chmod +x ./9-John_Doe
./9-John_Doe
```

**Expected output:**
```bash
# Before running the script
julien@ubuntu:/tmp/h$ ls -l hello
-rw-rw-r-- 1 julien julien 23 Sep 20 14:25 hello

# After running the script
julien@ubuntu:/tmp/h$ ./9-John_Doe
julien@ubuntu:/tmp/h$ ls -l hello
-rwxr-x-wx 1 julien julien 23 Sep 20 14:25 hello
```

**Command used:** `chmod 753 hello`

**Expected behavior:**
- Sets the mode of the file "hello" to `-rwxr-x-wx` (octal 753)
- Uses the `chmod` command with octal notation
- The permissions are: owner (rwx=7), group (r-x=5), others (-wx=3)
- File must exist in the current directory
- After running, the file has permissions 753
- Does not use commas in the command

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on shell permissions and user management fundamentals.
