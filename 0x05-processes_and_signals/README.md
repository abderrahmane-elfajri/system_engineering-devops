# 0x05. Processes and signals

This directory contains scripts that demonstrate processes and signals in Bash scripting.

## Files

### 0-what-is-my-pid
A Bash script that displays its own Process ID (PID).

**Usage:**
```bash
chmod +x ./0-what-is-my-pid
./0-what-is-my-pid
```

**Expected output:**
```
4120
```
(The actual PID number will vary each time the script is run)

**Requirements:**
- Displays only the PID number followed by a new line
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose

**Script structure:**
```bash
#!/usr/bin/env bash
# This script displays its own PID
echo $$
```

**Key concepts:**
- **Process ID (PID)**: Unique identifier assigned to each running process
- **`$$` variable**: Special bash variable containing the PID of the current shell
- **Process management**: PIDs are used for monitoring and controlling processes
- **System administration**: Understanding PIDs is fundamental for process management

**Technical details:**
- **`$$`**: Built-in bash variable that expands to the process ID of the shell
- **Dynamic value**: PID changes each time the script is executed
- **Process hierarchy**: Each process has a parent process ID (PPID) as well
- **Operating system**: Linux kernel assigns PIDs sequentially starting from 1

**Practical applications:**
- **Process monitoring**: Identifying specific processes for management
- **Script debugging**: Tracking which instance of a script is running
- **Log files**: Including PID in log entries for process tracking
- **Process control**: Using PID to send signals to specific processes

### 1-list_your_processes
A Bash script that displays a comprehensive list of all currently running processes on the system.

**Usage:**
```bash
chmod +x ./1-list_your_processes
./1-list_your_processes
```

**Expected output format:**
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         2  0.0  0.0      0     0 ?        S    Feb13   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Feb13   0:00  \_ [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    Feb13   0:00  \_ [kworker/0:0]
root         1  0.0  0.4  33608  2168 ?        Ss   Feb13   0:00 /sbin/init
root       373  0.0  0.0  19472   408 ?        S    Feb13   0:00 upstart-udev-bridge --daemon
```

**Requirements:**
- Shows all processes from all users
- Includes processes without TTY (background/system processes)
- Displays in user-oriented format with readable information
- Shows process hierarchy with indentation
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose

**Script structure:**
```bash
#!/usr/bin/env bash
# This script displays a list of currently running processes for all users
ps auxf
```

**Key concepts:**
- **ps command**: Primary tool for displaying process information
- **a**: Show processes for all users
- **u**: Display in user-oriented format
- **x**: Include processes without controlling terminal (TTY)
- **f**: Show full format listing (ASCII art process tree)
- **Process hierarchy**: Parent-child relationships shown with indentation

**Column explanations:**
- **USER**: Username of the process owner
- **PID**: Process ID (unique identifier)
- **%CPU**: Percentage of CPU usage
- **%MEM**: Percentage of memory usage
- **VSZ**: Virtual memory size in kilobytes
- **RSS**: Resident Set Size (physical memory used)
- **TTY**: Controlling terminal (? means no TTY)
- **STAT**: Process state (R=running, S=sleeping, Z=zombie, etc.)
- **START**: Time when process started
- **TIME**: Total CPU time consumed
- **COMMAND**: Command line that started the process

**Process states:**
- **R**: Running or runnable
- **S**: Interruptible sleep
- **D**: Uninterruptible sleep
- **T**: Stopped by job control signal
- **t**: Stopped by debugger
- **Z**: Zombie (terminated but not reaped)
- **<**: High priority process
- **N**: Low priority process
- **s**: Session leader

**Technical details:**
- **TTY processes**: Interactive processes attached to terminal
- **Non-TTY processes**: Background services, daemons, kernel threads
- **Process tree**: Shows parent-child relationships using ASCII art
- **System processes**: Kernel threads shown in square brackets [name]

### 2-show_your_bash_pid
A Bash script that displays only the lines containing the word "bash" from the process list, helping identify Bash shell PIDs.

**Usage:**
```bash
chmod +x ./2-show_your_bash_pid
./2-show_your_bash_pid
```

**Expected output format:**
```
sylvain   4404  0.0  0.7  21432  4000 pts/0    Ss   03:32   0:00          \_ -bash
sylvain   4477  0.0  0.2  11120  1352 pts/0    S+   03:40   0:00              \_ bash ./2-show_your_bash_PID
sylvain   4479  0.0  0.1  10460   912 pts/0    S+   03:40   0:00                  \_ grep bash
```

**Requirements:**
- Displays only lines containing the word "bash"
- Cannot use pgrep command
- Must use filtering with standard shell utilities
- Third line must be: `# shellcheck disable=SC2009`
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose

**Script structure:**
```bash
#!/usr/bin/env bash
# This script displays lines containing the word bash from the process list
# shellcheck disable=SC2009
ps auxf | grep bash
```

**Key concepts:**
- **Process filtering**: Using grep to filter specific processes
- **Pipeline**: Combining ps and grep commands with | operator
- **Pattern matching**: grep searches for "bash" in process command lines
- **Shell utilities**: Standard Unix tools for text processing
- **ShellCheck**: Code analysis tool for shell scripts

**Command breakdown:**
- **`ps auxf`**: Display all processes in user-oriented format with hierarchy
- **`|`**: Pipe operator to pass output to next command
- **`grep bash`**: Filter lines containing the word "bash"
- **Result**: Only bash-related processes are shown

**What you'll see:**
- **Parent bash shell**: Your main interactive shell session
- **Child bash processes**: Scripts currently running
- **grep process**: The grep command itself (shows in output)
- **Process hierarchy**: Indentation shows parent-child relationships

**ShellCheck disable comment:**
- **SC2009**: Warning about using ps with grep instead of pgrep
- **Disabled**: ALX task specifically requires this approach
- **Educational**: Shows common pattern before learning advanced alternatives
- **Line 3**: Must be exactly `# shellcheck disable=SC2009`

**Practical applications:**
- **Finding shell PID**: Identify your main bash shell process
- **Process debugging**: See which bash scripts are running
- **Resource monitoring**: Check CPU/memory usage of bash processes
- **Process management**: Get PIDs for sending signals to specific shells

**Understanding the output:**
- **First process**: Usually your main interactive shell (-bash)
- **Second process**: The script itself (bash ./2-show_your_bash_pid)
- **Third process**: The grep command (grep bash)
- **PID identification**: Second column shows the Process ID

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on processes and signals in Linux systems.
