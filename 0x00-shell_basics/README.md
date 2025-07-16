# 0x00. Shell, basics

This directory contains scripts that demonstrate basic shell operations and commands.

## Files

### 0-current_working_directory
A script that prints the absolute path name of the current working directory.

**Usage:**
```bash
chmod +x ./0-current_working_directory
./0-current_working_directory
```

**Expected output:**
```
/root/system_engineering-devops/0x00-shell_basics
```

The script uses the `pwd` command which stands for "print working directory" and displays the full absolute path of the current directory.

### 1-listit
A script that displays the contents list of your current directory.

**Usage:**
```bash
chmod +x ./1-listit
./1-listit
```

**Expected output:**
```
Applications    Documents   Dropbox Movies Pictures
Desktop Downloads   Library Music Public
```

The script uses the `ls` command which stands for "list" and displays all files and directories in the current working directory.

### 2-bring_me_home
A script that changes the working directory to the user's home directory.

**Usage:**
```bash
chmod +x ./2-bring_me_home
source ./2-bring_me_home
```

**Expected behavior:**
```bash
julien@ubuntu:/tmp$ pwd
/tmp
julien@ubuntu:/tmp$ source ./2-bring_me_home
julien@ubuntu:~$ pwd
/home/julien
```

The script uses the `cd` command without any arguments, which is the standard way to change to the home directory without using shell variables like $HOME.

### 3-listfiles
A script that displays the current directory contents in a long format.

**Usage:**
```bash
chmod +x ./3-listfiles
./3-listfiles
```

**Expected output:**
```
total 32
-rwxr-xr-x@ 1 sylvain staff 18 Jan 25 00:19 0-current_working_directory
-rwxr-xr-x@ 1 sylvain staff 19 Jan 25 00:23 1-listit
-rwxr-xr-x@ 1 sylvain staff 18 Jan 25 00:29 2-bring_me_home
-rwxr-xr-x@ 1 sylvain staff 18 Jan 25 00:39 3-listfiles
```

The script uses the `ls -l` command which displays detailed information about files including permissions, ownership, size, and modification date.

### 4-listmorefiles
A script that displays the current directory contents, including hidden files (those starting with .), in long format.

**Usage:**
```bash
chmod +x ./4-listmorefiles
./4-listmorefiles
```

**Expected output:**
```
total 32
drwxr-xr-x@ 6 sylvain staff 204 Jan 25 00:29 .
drwxr-xr-x@ 43 sylvain staff 1462 Jan 25 00:19 ..
-rwxr-xr-x@ 1 sylvain staff 18 Jan 25 00:19 0-current_working_directory
-rwxr-xr-x@ 1 sylvain staff 19 Jan 25 00:23 1-listit
-rwxr-xr-x@ 1 sylvain staff 18 Jan 25 00:29 2-bring_me_home
-rwxr-xr-x@ 1 sylvain staff 18 Jan 25 00:39 3-listfiles
-rwxr-xr-x@ 1 sylvain staff 18 Jan 25 00:41 4-listmorefiles
```

The script uses the `ls -la` command which displays detailed information about all files including hidden files (starting with .) in long format.

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on shell basics and Linux command line fundamentals.
