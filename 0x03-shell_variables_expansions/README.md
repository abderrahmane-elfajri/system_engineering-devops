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

### 4-global_variables
A script that lists all environment variables currently set in the shell session.

**Usage:**
```bash
chmod +x ./4-global_variables
./4-global_variables
```
or
```bash
source ./4-global_variables
```

**Expected output:**
```
CC=gcc
CDPATH=.:~:/usr/local:/usr:/
CFLAGS=-O2 -fomit-frame-pointer
COLORTERM=gnome-terminal
CXXFLAGS=-O2 -fomit-frame-pointer
DISPLAY=:0
DOMAIN=hq.garrels.be
EDITOR=vi
FCEDIT=vi
FIGNORE=.o:~
G_BROKEN_FILENAMES=1
GDK_USE_XFT=1
GDMSESSION=Default
GNOME_DESKTOP_SESSION_ID=Default
GTK_RC_FILES=/etc/gtk/gtkrc:/nethome/franky/.gtkrc-1.2-gnome2
GWMCOLOR=darkgreen
GWMTERM=xterm
HISTFILESIZE=5000
history_control=ignoredups
HISTSIZE=2000
HOME=/nethome/franky
HOSTNAME=octarine.hq.garrels.be
INPUTRC=/etc/inputrc
IRCNAME=franky
JAVA_HOME=/usr/java/j2sdk1.4.0
LANG=en_US
LDFLAGS=-s
LD_LIBRARY_PATH=/usr/lib/mozilla:/usr/lib/mozilla/plugins
LESSCHARSET=latin1
LESS=-edfMQ
LESSOPEN=|/usr/bin/lesspipe.sh %s
LEX=flex
LOCAL_MACHINE=octarine
LOGNAME=franky
[...]
```
(Output will vary based on your system's configuration)

**Command used:** `printenv`

**Expected behavior:**
- Lists all environment variables in the current shell session
- Each variable is displayed in the format `VARIABLE_NAME=value`
- Shows system-wide and user-specific environment variables
- Includes variables like PATH, HOME, USER, LANG, etc.
- Output varies depending on the system configuration and user settings
- Demonstrates how to access all environment variables at once

**Alternative commands:**
- `env` - also lists environment variables
- `set` - shows all variables (including shell variables, not just environment variables)

### 5-local_variables
A script that lists all local variables, environment variables, and shell functions.

**Usage:**
```bash
chmod +x ./5-local_variables
./5-local_variables
```
or
```bash
. ./5-local_variables
```

**Expected output:**
```
BASH=/bin/bash
BASHOPTS=checkwinsize:cmdhist:complete_fullquote:expand_aliases:extglob:extquote:force_fignore:histappend:interactive_comments:progcomp:promptvars:sourcepath
BASH_ALIASES=()
BASH_ARGC=()
BASH_ARGV=()
BASH_CMDS=()
BASH_COMPLETION_COMPAT_DIR=/etc/bash_completion.d
BASH_LINENO=()
BASH_REMATCH=()
BASH_SOURCE=()
BASH_VERSINFO=([0]="4" [1]="3" [2]="46" [3]="1" [4]="release" [5]="x86_64-pc-linux-gnu")
BASH_VERSION='4.3.46(1)-release'
CLUTTER_IM_MODULE=xim
COLUMNS=133
COMPIZ_CONFIG_PROFILE=ubuntu
COMP_WORDBREAKS=$' \t\n"\'><=;|&(:'
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-Fg27Lr20bq
DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path
DESKTOP_SESSION=ubuntu
[...]
```

**Command used:** `set`

**Expected behavior:**
- Lists all local variables specific to the current shell process
- Lists all environment variables (inherited by child processes)
- Lists all defined shell functions
- Shows more comprehensive output than `printenv` or `env`
- Includes shell-specific variables like BASH_VERSION, BASH_ALIASES, etc.
- Displays arrays and functions in addition to simple variables
- Output varies depending on the shell configuration and defined functions

**What `set` shows:**
1. **Environment Variables**: Like PATH, HOME, USER (also shown by `printenv`)
2. **Local Variables**: Shell-specific variables not exported to child processes
3. **Shell Functions**: User-defined and system functions
4. **Arrays**: Bash arrays and associative arrays
5. **Shell Options**: Various bash settings and configurations

**Comparison with other commands:**
- `printenv`/`env`: Shows only environment variables
- `set`: Shows everything (local variables + environment variables + functions)
- `declare`: Similar to `set` but with type information

### 6-create_local_variable
A script that creates a new local variable named `BEST` with the value `School`.

**Usage:**
```bash
source ./6-create_local_variable
```
or
```bash
. ./6-create_local_variable
```

**Expected behavior:**
- Creates a local variable `BEST` with the value `School`
- The variable is only available in the current shell session
- Must be sourced (not executed) to make the variable available in the current shell
- The variable is not exported, so it won't be inherited by child processes

**Variable specifications:**
- **Name**: BEST
- **Value**: School
- **Type**: Local variable (not environment variable)

**Command used:** `BEST="School"`

**Verification:**
After sourcing the script, you can verify the variable exists:
```bash
$ . ./6-create_local_variable
$ echo $BEST
School
```

**Important notes:**
- This creates a local variable, not an environment variable
- Local variables are specific to the current shell process
- They are not inherited by child processes (unlike environment variables created with `export`)
- The script must be sourced to affect the current shell environment
- Simple assignment syntax `VARIABLE="value"` creates local variables

**Difference from environment variables:**
- Local variable: `BEST="School"` (available only in current shell)
- Environment variable: `export BEST="School"` (inherited by child processes)

### 7-create_global_variable
A script that creates a new global variable (environment variable) named `BEST` with the value `School`.

**Usage:**
```bash
source ./7-create_global_variable
```
or
```bash
. ./7-create_global_variable
```

**Expected behavior:**
- Creates a global variable `BEST` with the value `School`
- The variable is exported to the environment, making it available to child processes
- Must be sourced (not executed) to make the variable available in the current shell
- The variable will be inherited by any child processes spawned from the current shell

**Variable specifications:**
- **Name**: BEST
- **Value**: School
- **Type**: Global variable (environment variable)

**Command used:** `export BEST="School"`

**Verification:**
After sourcing the script, you can verify the variable exists and is exported:
```bash
$ . ./7-create_global_variable
$ echo $BEST
School
$ printenv | grep BEST
BEST=School
```

**Important notes:**
- This creates a global variable (environment variable), not just a local variable
- Global variables are inherited by child processes
- The `export` command makes the variable available to the environment
- The script must be sourced to affect the current shell environment
- Exported variables appear in `printenv` output

**Difference from local variables:**
- Local variable: `BEST="School"` (available only in current shell)
- Global variable: `export BEST="School"` (inherited by child processes)

**Key concept:**
- **Local variables**: Confined to the current shell session
- **Global variables**: Passed on to child processes, making them accessible to programs and scripts

### 8-true_knowledge
A script that prints the result of adding 128 to the value stored in the environment variable `TRUEKNOWLEDGE`.

**Usage:**
```bash
export TRUEKNOWLEDGE=1209
chmod +x ./8-true_knowledge
./8-true_knowledge
```

**Expected output:**
```
1337
```
(Result of TRUEKNOWLEDGE + 128)

**Example:**
```bash
julien@production-503e7013:~$ export TRUEKNOWLEDGE=1209
julien@production-503e7013:~$ ./8-true_knowledge | cat -e
1337$
julien@production-503e7013:~$
```

**Command used:** `echo $((TRUEKNOWLEDGE + 128))`

**Expected behavior:**
- Reads the value from the environment variable `TRUEKNOWLEDGE`
- Adds 128 to that value using arithmetic expansion
- Prints the result followed by a newline
- Uses `$((expression))` for arithmetic operations in bash
- Assumes `TRUEKNOWLEDGE` contains a numeric value

**Important notes:**
- The `TRUEKNOWLEDGE` variable must be set in the environment before execution
- Uses arithmetic expansion `$((TRUEKNOWLEDGE + 128))` for the calculation
- The result is automatically followed by a newline from `echo`
- Demonstrates accessing environment variables and performing arithmetic operations

**Arithmetic expansion syntax:**
- `$((variable + number))` performs addition
- Variables inside `$(())` don't need the `$` prefix
- Supports basic arithmetic operations: `+`, `-`, `*`, `/`, `%`

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on shell variables, expansions, and aliases.
