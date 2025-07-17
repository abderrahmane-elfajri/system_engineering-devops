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

### 3-twofiles
A script that displays the content of `/etc/passwd` and `/etc/hosts` files.

**Usage:**
```bash
chmod +x ./3-twofiles
./3-twofiles
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
##
# Host Database
#
# localhost is used to configure the loopback interface
# when the system is booting. Do not change this entry.
##
127.0.0.1   localhost
255.255.255.255 broadcasthost
::1 localhost
```

**Command used:** `cat /etc/passwd /etc/hosts`

**Expected behavior:**
- Displays the content of both `/etc/passwd` and `/etc/hosts` files
- Uses the `cat` command with multiple file arguments
- The files are displayed one after another (concatenated)
- `/etc/passwd` contains user account information
- `/etc/hosts` contains hostname to IP address mappings
- The output will vary depending on the system configuration

### 4-lastlines
A script that displays the last 10 lines of `/etc/passwd`.

**Usage:**
```bash
chmod +x ./4-lastlines
./4-lastlines
```

**Expected output:**
```
_assetcache:*:235:235:Asset Cache Service:/var/empty:/usr/bin/false
_coremediaiod:*:236:236:Core Media IO Daemon:/var/empty:/usr/bin/false
_launchservicesd:*:239:239:_launchservicesd:/var/empty:/usr/bin/false
_iconservices:*:240:240:IconServices:/var/empty:/usr/bin/false
_distnote:*:241:241:DistNote:/var/empty:/usr/bin/false
_nsurlsessiond:*:242:242:NSURLSession Daemon:/var/db/nsurlsessiond:/usr/bin/false
_nsurlstoraged:*:243:243:NSURLStorage Daemon:/var/empty:/usr/bin/false
_displaypolicyd:*:244:244:Display Policy Daemon:/var/empty:/usr/bin/false
_astris:*:245:245:Astris Services:/var/db/astris:/usr/bin/false
_krbfast:*:246:-2:Kerberos FAST Account:/var/empty:/usr/bin/false
```

**Command used:** `tail /etc/passwd`

**Expected behavior:**
- Displays the last 10 lines of `/etc/passwd` file
- Uses the `tail` command which shows the end of a file
- By default, `tail` displays the last 10 lines
- The hint "Think of it as a cat, what is at the end of it?" refers to the tail
- Shows the most recently added user accounts in the system
- The output will vary depending on the system's user accounts

### 5-firstlines
A script that displays the first 10 lines of `/etc/passwd`.

**Usage:**
```bash
chmod +x ./5-firstlines
./5-firstlines
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
```

**Command used:** `head /etc/passwd`

**Expected behavior:**
- Displays the first 10 lines of `/etc/passwd` file
- Uses the `head` command which shows the beginning of a file
- By default, `head` displays the first 10 lines
- Shows the header comments and first few user accounts in the system
- Complementary to the `tail` command used in the previous task
- The output will vary depending on the system's configuration

### 6-third_line
A script that displays the third line of the file `iacta`.

**Usage:**
```bash
chmod +x ./6-third_line
./6-third_line
```

**Expected output:**
```
Alea iacta est ("The die is cast") is a Latin phrase attributed by Suetonius
```

**Command used:** `head -3 iacta | tail -1`

**Expected behavior:**
- Displays only the third line of the file `iacta`
- Uses `head -3` to get the first 3 lines, then pipes to `tail -1` to get the last line of those 3
- Does not use `sed` as specified in the requirements
- The file `iacta` must be in the working directory
- The output will vary depending on the content of the file `iacta`
- This technique combines `head` and `tail` with piping to extract a specific line

**How it works:**
1. `head -3 iacta` gets the first 3 lines of the file
2. `|` pipes that output to the next command
3. `tail -1` gets the last line from the piped input (which is the 3rd line of the original file)

### 7-file
A script that creates a file named exactly `*\'"Best School"\'*$\?*****:)`, containing the text "Best School", and ending with a new line.

**Usage:**
```bash
chmod +x ./7-file
./7-file
```

**Expected output:**
```bash
# After running the script, a file with the complex name will be created
julien@ubuntu:~/shell$ ls -l
-rw-rw-r-- 1 julien julien 17 Jan 20 06:40 '\*\\'"Best School"\'\\*$\?\*\*\*\*\*:)'

# The file contains:
julien@ubuntu:~/shell$ cat -e \\*
Best School$
```

**Command used:** `echo "Best School" > \*\\\'\"Best\ School\"\\\'\*\$\\\?\*\*\*\*\*\:\)`

**Expected behavior:**
- Creates a file with the exact name `*\'"Best School"\'*$\?*****:)`
- The filename contains many special characters that need to be escaped
- Uses `echo` to write "Best School" to the file
- The `>` operator redirects output to create the file
- Each special character in the filename is properly escaped with backslashes
- The file contains "Best School" followed by a newline
- Demonstrates advanced shell escaping techniques

**Special characters escaped:**
- `*` → `\*`
- `\` → `\\`
- `'` → `\'`
- `"` → `\"`
- `$` → `\$`
- `?` → `\?`
- `:` → `\:`
- `)` → `\)`
- Space → `\ `

### 8-cwd_state
A script that writes into the file `ls_cwd_content` the result of the command `ls -la`. If the file already exists, it should be overwritten. If it doesn't exist, it should be created.

**Usage:**
```bash
chmod +x ./8-cwd_state
./8-cwd_state
```

**Expected output:**
```bash
# After running the script, ls_cwd_content file is created/overwritten
julien@ubuntu:/tmp/h$ ls -la
total 24
drwxrwxr-x  2 julien julien 4096 Sep 20 18:18 .
drwxrwxrwt 13 root   root   4096 Sep 20 18:18 ..
-rwxrw-r--  1 julien julien   36 Sep 20 18:18 8-cwd_state
-rw-rw-r--  1 betty  julien   23 Sep 20 14:25 hello
-rw-rw-r--  1 julien julien  926 Sep 20 17:52 iacta
-rw-rw-r--  1 julien julien  329 Sep 20 18:18 ls_cwd_content

# The file contains the directory listing:
julien@ubuntu:/tmp/h$ cat ls_cwd_content 
total 20
drwxrwxr-x  2 julien julien 4096 Sep 20 18:18 .
drwxrwxrwt 13 root   root   4096 Sep 20 18:18 ..
-rwxrw-r--  1 julien julien   36 Sep 20 18:18 8-cwd_state
-rw-rw-r--  1 betty  julien   23 Sep 20 14:25 hello
-rw-rw-r--  1 julien julien  926 Sep 20 17:52 iacta
-rw-rw-r--  1 julien julien    0 Sep 20 18:18 ls_cwd_content
```

**Command used:** `ls -la > ls_cwd_content`

**Expected behavior:**
- Executes `ls -la` to list all files and directories in long format
- Uses `>` redirection operator to write output to `ls_cwd_content`
- The `>` operator overwrites the file if it exists, creates it if it doesn't
- Saves the current state of the directory for later reference
- The output includes detailed file information (permissions, owner, size, date)
- Note: The file `ls_cwd_content` will appear as size 0 in its own listing because the redirection happens before the file is written

### 9-duplicate_last_line
A script that duplicates the last line of the file `iacta`.

**Usage:**
```bash
chmod +x ./9-duplicate_last_line
./9-duplicate_last_line
```

**Expected output:**
```bash
# Before running the script
julien@ubuntu:/tmp/h$ cat iacta 
Alea iacta est

Alea iacta est ("The die is cast") is a Latin phrase attributed by Suetonius
(as iacta alea est) to Julius Caesar on January 10, 49 BC
as he led his army across the Rubicon river in Northern Italy. With this step,
he entered Italy at the head of his army in defiance of the Senate and began
his long civil war against Pompey and the Optimates. The phrase has been
adopted in Italian (Il dado è tratto), Romanian (Zarurile au fost aruncate),
Spanish (La suerte está echada), French (Les dés sont jetés), Portuguese (A
sorte está lançada), Dutch (De teerling is geworpen),
German (Der Würfel ist gefallen), Hungarian (A kocka el van vetve) and many other languages to
indicate that events have passed a point of no return.

Read more: https://en.wikipedia.org/wiki/Alea_iacta_est

# After running the script
julien@ubuntu:/tmp/h$ cat iacta 
Alea iacta est

Alea iacta est ("The die is cast") is a Latin phrase attributed by Suetonius
(as iacta alea est) to Julius Caesar on January 10, 49 BC
as he led his army across the Rubicon river in Northern Italy. With this step,
he entered Italy at the head of his army in defiance of the Senate and began
his long civil war against Pompey and the Optimates. The phrase has been
adopted in Italian (Il dado è tratto), Romanian (Zarurile au fost aruncate),
Spanish (La suerte está echada), French (Les dés sont jetés), Portuguese (A
sorte está lançada), Dutch (De teerling is geworpen),
German (Der Würfel ist gefallen), Hungarian (A kocka el van vetve) and many other languages to
indicate that events have passed a point of no return.

Read more: https://en.wikipedia.org/wiki/Alea_iacta_est
Read more: https://en.wikipedia.org/wiki/Alea_iacta_est
```

**Command used:** `tail -1 iacta >> iacta`

**Expected behavior:**
- Gets the last line of the file `iacta` using `tail -1`
- Appends that line to the same file using `>>` (append redirection)
- The `>>` operator appends to the file without overwriting existing content
- Results in the last line being duplicated at the end of the file
- The file `iacta` must exist in the working directory
- Works regardless of the content of the file

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on shell I/O redirections and filters.
