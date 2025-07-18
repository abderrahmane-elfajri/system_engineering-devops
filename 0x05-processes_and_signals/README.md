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

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on processes and signals in Linux systems.
