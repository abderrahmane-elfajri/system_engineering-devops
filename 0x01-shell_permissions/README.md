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

### 11-directories_permissions
A script that adds execute permission to all subdirectories of the current directory for the owner, the group owner and all other users. Regular files should not be changed.

**Usage:**
```bash
chmod +x ./11-directories_permissions
./11-directories_permissions
```

**Expected output:**
```bash
# Before running the script
julien@ubuntu:/tmp/h$ ls -l
total 20
-rwxrwxr-x 1 julien julien   24 Sep 20 14:53 11-directories_permissions
drwx------ 2 julien julien 4096 Sep 20 14:49 dir0
drwx------ 2 julien julien 4096 Sep 20 14:49 dir1
drwx------ 2 julien julien 4096 Sep 20 14:49 dir2
-rw-rw-r-- 1 julien julien   23 Sep 20 14:25 hello

# After running the script
julien@ubuntu:/tmp/h$ ./11-directories_permissions 
julien@ubuntu:/tmp/h$ ls -l
total 20
-rwxrwxr-x 1 julien julien   24 Sep 20 14:53 11-directories_permissions
drwx--x--x 2 julien julien 4096 Sep 20 14:49 dir0
drwx--x--x 2 julien julien 4096 Sep 20 14:49 dir1
drwx--x--x 2 julien julien 4096 Sep 20 14:49 dir2
-rw-rw-r-- 1 julien julien   23 Sep 20 14:25 hello
```

**Command used:** `chmod a+X *`

**Expected behavior:**
- Adds execute permission to all subdirectories for owner, group, and others
- Uses the `chmod` command with `a+X` (capital X)
- `a` means "all" (owner, group, others)
- `+X` adds execute permission only to directories and files that already have execute permission for someone
- Regular files without execute permission remain unchanged
- The `*` wildcard applies to all items in the current directory
- Only directories get the execute permission added

### 12-directory_permissions
A script that creates a directory called `my_dir` with permissions 751 in the working directory.

**Usage:**
```bash
chmod +x ./12-directory_permissions
./12-directory_permissions
```

**Expected output:**
```bash
# Before running the script
julien@ubuntu:/tmp/h$ ls -l
total 20
-rwxrwxr-x 1 julien julien   39 Sep 20 14:59 12-directory_permissions
drwx--x--x 2 julien julien 4096 Sep 20 14:49 dir0
drwx--x--x 2 julien julien 4096 Sep 20 14:49 dir1
drwx--x--x 2 julien julien 4096 Sep 20 14:49 dir2
-rw-rw-r-- 1 julien julien   23 Sep 20 14:25 hello

# After running the script
julien@ubuntu:/tmp/h$ ./12-directory_permissions
julien@ubuntu:/tmp/h$ ls -l
total 24
-rwxrwxr-x 1 julien julien   39 Sep 20 14:59 12-directory_permissions
drwx--x--x 2 julien julien 4096 Sep 20 14:49 dir0
drwx--x--x 2 julien julien 4096 Sep 20 14:49 dir1
drwx--x--x 2 julien julien 4096 Sep 20 14:49 dir2
drwxr-x--x 2 julien julien 4096 Sep 20 14:59 my_dir
-rw-rw-r-- 1 julien julien   23 Sep 20 14:25 hello
```

**Command used:** `mkdir -m 751 my_dir`

**Expected behavior:**
- Creates a directory called `my_dir` with permissions 751
- Uses the `mkdir` command with the `-m` option to set permissions during creation
- Permissions 751 means: owner (rwx=7), group (r-x=5), others (--x=1)
- The directory is created in the current working directory

### 13-change_group
A script that changes the group owner to `school` for the file `hello`.

**Usage:**
```bash
chmod +x ./13-change_group
sudo ./13-change_group
```

**Expected output:**
```bash
# Before running the script
julien@ubuntu:/tmp/h$ ls -l
total 24
-rwxrwxr-x 1 julien julien      34 Sep 20 15:03 13-change_group
drwx--x--x 2 julien julien    4096 Sep 20 14:49 dir0
drwx--x--x 2 julien julien    4096 Sep 20 14:49 dir1
drwx--x--x 2 julien julien    4096 Sep 20 14:49 dir2
drwxr-x--x 2 julien julien    4096 Sep 20 14:59 my_dir
-rw-rw-r-- 1 julien school   23 Sep 20 14:25 hello

# After running the script
julien@ubuntu:/tmp/h$ sudo ./13-change_group
julien@ubuntu:/tmp/h$ ls -l
total 24
-rwxrwxr-x 1 julien julien      34 Sep 20 15:03 13-change_group
drwx--x--x 2 julien julien    4096 Sep 20 14:49 dir0
drwx--x--x 2 julien julien    4096 Sep 20 14:49 dir1
drwx--x--x 2 julien julien    4096 Sep 20 14:49 dir2
drwxr-x--x 2 julien julien    4096 Sep 20 14:59 my_dir
-rw-rw-r-- 1 julien school   23 Sep 20 14:25 hello
```

**Command used:** `chgrp school hello`

**Expected behavior:**
- Changes the group owner of the file `hello` to `school`
- Uses the `chgrp` command (change group)
- The file `hello` must exist in the current directory
- May require sudo privileges depending on current user permissions
- Only the group ownership changes, file permissions remain the same

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on shell permissions and user management fundamentals.
