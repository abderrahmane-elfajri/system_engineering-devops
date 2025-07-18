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

### 3-show_your_bash_pid_made_easy
A Bash script that displays the PID and process name of processes containing "bash" using a more direct approach.

**Usage:**
```bash
chmod +x ./3-show_your_bash_pid_made_easy
./3-show_your_bash_pid_made_easy
```

**Expected output format:**
```
4404 bash
4555 bash
```

**Requirements:**
- Cannot use the ps command
- Must use a different command that queries processes by name
- Output format: PID process_name (space-separated)
- Shows only processes whose name contains "bash"
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose

**Script structure:**
```bash
#!/usr/bin/env bash
# This script displays PID and process name of processes whose name contains bash
pgrep -l bash
```

**Key concepts:**
- **pgrep command**: Process grep - searches for processes by name
- **-l flag**: List format showing PID and process name
- **Direct querying**: More efficient than ps + grep combination
- **Pattern matching**: Finds processes containing "bash" in their name
- **Concise output**: Shows only PID and process name

**Command breakdown:**
- **`pgrep`**: Process grep utility for finding processes by name
- **`-l`**: List format (PID process_name)
- **`bash`**: Pattern to search for in process names
- **Result**: Clean output with PID and process name only

**Advantages over ps + grep:**
- **More efficient**: Direct process query instead of full listing + filtering
- **Cleaner output**: No extra information like CPU, memory usage
- **Purpose-built**: Designed specifically for finding processes by name
- **No false positives**: Won't show grep process itself
- **Simpler syntax**: Single command instead of pipeline

**What you'll see:**
- **Parent bash shell**: Your main interactive shell session
- **Script process**: The current bash script running
- **Variable PIDs**: Process IDs change each time script runs
- **Consistent format**: Always "PID process_name"

**Practical applications:**
- **Quick PID lookup**: Fast way to find specific process IDs
- **Automation scripts**: Easy to parse output for further processing
- **Process monitoring**: Check if specific processes are running
- **System administration**: Identify processes for management tasks

**Comparison with previous task:**
- **Task 2**: `ps auxf | grep bash` - Full process info with filtering
- **Task 3**: `pgrep -l bash` - Direct, concise process lookup
- **Evolution**: From general-purpose to specialized tools

### 4-to_infinity_and_beyond
A Bash script that displays "To infinity and beyond" indefinitely in an infinite loop with 2-second pauses.

**Usage:**
```bash
chmod +x ./4-to_infinity_and_beyond
./4-to_infinity_and_beyond
```

**Expected output:**
```
To infinity and beyond
To infinity and beyond
To infinity and beyond
To infinity and beyond
To infinity and beyond
^C
```
(Continues until manually stopped with Ctrl+C)

**Requirements:**
- Runs in an infinite loop
- Displays "To infinity and beyond" continuously
- Pauses for 2 seconds between each display
- Must be stopped manually with Ctrl+C
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose

**Script structure:**
```bash
#!/usr/bin/env bash
# This script displays "To infinity and beyond" indefinitely
while true
do
    echo "To infinity and beyond"
    sleep 2
done
```

**Key concepts:**
- **Infinite loop**: `while true` creates a loop that never terminates naturally
- **Sleep command**: `sleep 2` pauses execution for 2 seconds
- **Signal handling**: Ctrl+C sends SIGINT to terminate the process
- **Continuous execution**: Loop runs indefinitely until interrupted
- **Process control**: Manual intervention required to stop

**Command breakdown:**
- **`while true`**: Infinite loop condition (always evaluates to true)
- **`do...done`**: Loop body containing commands to execute
- **`echo`**: Displays the message to standard output
- **`sleep 2`**: Pauses execution for 2 seconds
- **`Ctrl+C`**: Sends SIGINT signal to terminate the process

**Infinite loop patterns:**
- **`while true`**: Most common and readable
- **`while :`**: Alternative using colon (: is always true)
- **`for (( ; ; ))`**: C-style infinite loop
- **`until false`**: Loops until false (which never happens)

**Practical applications:**
- **Service monitoring**: Continuously check system status
- **Log monitoring**: Watch log files for changes
- **Server processes**: Keep services running indefinitely
- **Periodic tasks**: Execute commands at regular intervals
- **System daemons**: Background processes that run continuously

**Safety considerations:**
- **CPU usage**: Sleep prevents excessive CPU consumption
- **Resource management**: Infinite loops can consume system resources
- **Signal handling**: Always ensure processes can be terminated
- **Error handling**: Consider what happens if commands fail

**Stopping the script:**
- **Ctrl+C**: Sends SIGINT (interrupt signal)
- **Ctrl+Z**: Sends SIGTSTP (suspend signal)
- **kill command**: Can terminate by PID
- **killall command**: Can terminate by process name

**Signal concepts:**
- **SIGINT**: Interrupt signal (Ctrl+C)
- **SIGTERM**: Termination signal (graceful shutdown)
- **SIGKILL**: Force kill signal (cannot be caught)
- **Process termination**: How to stop infinite loops safely

### 5-dont_stop_me_now
A Bash script that stops the 4-to_infinity_and_beyond process using the kill command.

**Usage:**
```bash
chmod +x ./5-dont_stop_me_now
./5-dont_stop_me_now
```

**Testing scenario:**
Terminal #0 (Start the infinite loop):
```bash
./4-to_infinity_and_beyond
To infinity and beyond
To infinity and beyond
To infinity and beyond
To infinity and beyond
Terminated
```

Terminal #1 (Kill the process):
```bash
./5-dont_stop_me_now
```

**Requirements:**
- Must use the kill command
- Must find the PID of the 4-to_infinity_and_beyond process
- Terminates the running infinite loop process
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose

**Script structure:**
```bash
#!/usr/bin/env bash
# This script stops the 4-to_infinity_and_beyond process
kill "$(pgrep -f "4-to_infinity_and_beyond")"
```

**Key concepts:**
- **kill command**: Sends signals to processes to terminate them
- **pgrep -f**: Finds processes by full command line (not just process name)
- **Command substitution**: `$(command)` executes command and uses its output
- **Process termination**: Programmatic way to stop processes
- **Signal sending**: Default kill sends SIGTERM (graceful termination)

**Command breakdown:**
- **`pgrep -f "4-to_infinity_and_beyond"`**: Finds PID of process containing this string
- **`-f`**: Search full command line, not just process name
- **`$()`**: Command substitution - executes pgrep and returns PID
- **`kill`**: Sends SIGTERM signal to the process ID
- **`"$(...)"`**: Quotes ensure proper handling of PID

**Why use pgrep -f:**
- **Full command search**: Matches script name in command line
- **Precise targeting**: Finds exact process we want to kill
- **Dynamic PID**: Works regardless of what PID the process has
- **Automated**: No need to manually find PID first

**Process termination flow:**
1. **pgrep -f**: Searches for process containing "4-to_infinity_and_beyond"
2. **Returns PID**: Gets the process ID number
3. **kill**: Sends SIGTERM signal to that PID
4. **Process stops**: The infinite loop terminates gracefully

**Signal types:**
- **SIGTERM (15)**: Default kill signal, graceful termination
- **SIGKILL (9)**: Force kill, cannot be caught or ignored
- **SIGINT (2)**: Interrupt signal (same as Ctrl+C)
- **SIGSTOP (19)**: Suspend process (cannot be caught)

**Alternative approaches:**
- **Manual method**: `ps aux | grep 4-to_infinity_and_beyond` then `kill PID`
- **pkill command**: `pkill -f "4-to_infinity_and_beyond"`
- **killall command**: `killall 4-to_infinity_and_beyond`

**Practical applications:**
- **Process management**: Stop runaway or stuck processes
- **Service control**: Terminate specific services programmatically
- **Script automation**: Stop processes as part of larger scripts
- **System maintenance**: Clean up processes during maintenance
- **Emergency situations**: Stop processes consuming too many resources

**Safety considerations:**
- **Process identification**: Make sure you're killing the right process
- **Signal choice**: Use SIGTERM first, SIGKILL as last resort
- **Error handling**: Check if process exists before trying to kill
- **Permissions**: May need appropriate permissions to kill processes

### 6-stop_me_if_you_can
A Bash script that stops the 4-to_infinity_and_beyond process using an alternative method to kill/killall.

**Usage:**
```bash
chmod +x ./6-stop_me_if_you_can
./6-stop_me_if_you_can
```

**Testing scenario:**
Terminal #0 (Start the infinite loop):
```bash
./4-to_infinity_and_beyond
To infinity and beyond
To infinity and beyond
To infinity and beyond
To infinity and beyond
Terminated
```

Terminal #1 (Stop the process):
```bash
./6-stop_me_if_you_can
```

**Requirements:**
- Cannot use kill command
- Cannot use killall command
- Must find and stop the 4-to_infinity_and_beyond process
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose

**Script structure:**
```bash
#!/usr/bin/env bash
# This script stops the 4-to_infinity_and_beyond process
pkill -f "4-to_infinity_and_beyond"
```

**Key concepts:**
- **pkill command**: Process kill - terminates processes by name pattern
- **Alternative method**: Different approach from kill/killall commands
- **Pattern matching**: Uses -f flag to search full command line
- **Direct termination**: Single command to find and kill process
- **Process management**: Alternative tools for process control

**Command breakdown:**
- **`pkill`**: Process kill utility for terminating processes by pattern
- **`-f`**: Search full command line, not just process name
- **`"4-to_infinity_and_beyond"`**: Pattern to match in process command line
- **Result**: Terminates matching process directly

**Advantages of pkill:**
- **Single command**: Combines search and kill in one operation
- **Pattern matching**: Flexible process identification
- **No PID required**: Don't need to find PID first
- **Efficient**: Direct process termination
- **Versatile**: Can kill multiple matching processes

**Comparison with previous methods:**
- **Task 5**: `kill "$(pgrep -f "...")"`  - Two-step process (find PID, then kill)
- **Task 6**: `pkill -f "..."`  - Single-step process (find and kill together)
- **Evolution**: From manual PID lookup to integrated process control

**Alternative methods (not used here):**
- **kill + pgrep**: Find PID then kill (previous task)
- **killall**: Kill by process name (forbidden)
- **skill**: System V kill command (deprecated)
- **/proc filesystem**: Direct signal writing (advanced)

**Signal behavior:**
- **Default signal**: pkill sends SIGTERM (graceful termination)
- **Signal options**: Can specify different signals with -SIGNAL
- **Process response**: Process can catch and handle SIGTERM
- **Termination**: Process stops execution and exits

**Pattern matching details:**
- **-f flag**: Searches entire command line including arguments
- **Exact match**: Finds processes containing the exact string
- **Case sensitive**: Pattern matching is case-sensitive
- **Multiple matches**: Will kill all matching processes

**Practical applications:**
- **Service management**: Stop services by name pattern
- **Script automation**: Terminate processes in automated scripts
- **System maintenance**: Clean up processes during maintenance
- **Emergency control**: Quick process termination
- **Batch operations**: Kill multiple related processes at once

**Safety considerations:**
- **Pattern precision**: Make sure pattern matches only intended processes
- **Multiple matches**: Be aware pkill can kill multiple processes
- **Process verification**: Check what processes match before killing
- **Testing**: Test patterns carefully to avoid unintended termination

### 7-highlander
A Bash script that displays "To infinity and beyond" indefinitely while demonstrating signal handling by catching and responding to SIGTERM signals.

**Usage:**
```bash
chmod +x ./7-highlander
./7-highlander
```

**Testing scenario:**
Terminal #0 (Start the highlander):
```bash
./7-highlander
To infinity and beyond
To infinity and beyond
To infinity and beyond
I am invincible!!!
To infinity and beyond
To infinity and beyond
To infinity and beyond
I am invincible!!!
To infinity and beyond
```

Terminal #1 (Try to stop with kill):
```bash
kill <PID_of_7-highlander>
```

**Requirements:**
- Displays "To infinity and beyond" indefinitely
- Catches SIGTERM signal and displays "I am invincible!!!"
- Continues running after receiving SIGTERM
- Uses trap to handle signal gracefully
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose

**Script structure:**
```bash
#!/usr/bin/env bash
# This script displays "To infinity and beyond" indefinitely and handles SIGTERM signal
trap 'echo "I am invincible!!!"' SIGTERM

while true
do
    echo "To infinity and beyond"
    sleep 2
done
```

**Key concepts:**
- **Signal handling**: Using trap to catch and respond to signals
- **SIGTERM signal**: Standard termination signal (signal 15)
- **Signal trapping**: Intercepting signals before they terminate the process
- **Resilient processes**: Processes that continue running despite termination attempts
- **Custom signal response**: Defining what happens when signal is received

**Command breakdown:**
- **`trap 'command' SIGNAL`**: Sets up signal handler for specified signal
- **`'echo "I am invincible!!!"'`**: Command executed when SIGTERM received
- **`SIGTERM`**: Signal to trap (termination signal)
- **`while true`**: Infinite loop continues running
- **Signal flow**: SIGTERM → trap → message → continue loop

**Signal trapping details:**
- **trap command**: Built-in bash command for signal handling
- **Signal names**: Can use SIGTERM, TERM, or number 15
- **Handler execution**: Trap command executes when signal received
- **Process continuation**: After handler runs, process continues normally
- **Signal masking**: Trap effectively "masks" the signal's default behavior

**What happens when SIGTERM is sent:**
1. **Signal reception**: Process receives SIGTERM signal
2. **Trap activation**: Bash executes the trap command
3. **Message display**: "I am invincible!!!" is printed
4. **Loop continuation**: while loop continues running
5. **Default behavior**: Signal doesn't terminate the process

**Types of signals:**
- **SIGTERM (15)**: Graceful termination request (can be trapped)
- **SIGKILL (9)**: Force kill (cannot be trapped or ignored)
- **SIGINT (2)**: Interrupt signal from Ctrl+C (can be trapped)
- **SIGSTOP (19)**: Suspend process (cannot be trapped)
- **SIGHUP (1)**: Hangup signal (can be trapped)

**Practical applications:**
- **Service daemons**: Handle shutdown requests gracefully
- **Cleanup operations**: Perform cleanup before termination
- **Resource management**: Close files, connections before exit
- **Logging**: Log termination attempts for security monitoring
- **State preservation**: Save current state before shutdown

**Signal handling best practices:**
- **Graceful cleanup**: Use trap to clean up resources
- **Multiple signals**: Handle different signals appropriately
- **Restoration**: Restore terminal state if modified
- **Error handling**: Consider what happens if cleanup fails
- **Documentation**: Document signal handling behavior

**Testing the script:**
- **Start script**: Run ./7-highlander in one terminal
- **Find PID**: Use ps, pgrep, or another method to find process ID
- **Send SIGTERM**: Use kill <PID> to send termination signal
- **Observe behavior**: Script shows message but continues running
- **Force kill**: Use kill -9 <PID> to force termination

**Limitations:**
- **SIGKILL immunity**: Cannot trap SIGKILL (kill -9)
- **SIGSTOP immunity**: Cannot trap SIGSTOP
- **System limits**: System can still force termination
- **Resource limits**: Process can be killed for resource violations

### 67-stop_me_if_you_can
A Bash script that stops the 7-highlander process using pkill, demonstrating that even signal-handling processes can be terminated with the right approach.

**Usage:**
```bash
chmod +x ./67-stop_me_if_you_can
./67-stop_me_if_you_can
```

**Testing scenario:**
Terminal #0 (Start the highlander):
```bash
./7-highlander
To infinity and beyond
To infinity and beyond
To infinity and beyond
I am invincible!!!
To infinity and beyond
To infinity and beyond
Killed
```

Terminal #1 (Stop the highlander):
```bash
./67-stop_me_if_you_can
```

**Requirements:**
- Must stop the 7-highlander process completely
- Cannot use kill command
- Cannot use killall command
- Must terminate the signal-handling process
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose

**Script structure:**
```bash
#!/usr/bin/env bash
# This script stops the 7-highlander process
pkill -f "7-highlander"
```

**Key concepts:**
- **Process termination**: Even signal-handling processes can be stopped
- **pkill effectiveness**: pkill can terminate trapped processes
- **Signal override**: Some termination methods bypass signal handlers
- **Process management**: Administrative control over running processes
- **Pattern matching**: Using filename patterns to identify processes

**Why this works:**
- **SIGTERM by default**: pkill sends SIGTERM first (which gets trapped)
- **Process cleanup**: pkill may use additional mechanisms
- **System enforcement**: Operating system can override process behavior
- **Multiple attempts**: pkill may retry with different signals
- **Administrative power**: System tools have privileges to terminate processes

**Command breakdown:**
- **`pkill`**: Process kill utility for pattern-based termination
- **`-f`**: Search full command line including script name
- **`"7-highlander"`**: Pattern to match the highlander process
- **Result**: Terminates the process despite signal handling

**Signal handling vs. process termination:**
- **Signal trapping**: Process can catch and handle some signals
- **System override**: Operating system can force termination
- **Administrative tools**: System utilities have enhanced privileges
- **Process limits**: Even trapped processes have termination mechanisms
- **Resource management**: System protects itself from runaway processes

**Practical applications:**
- **System administration**: Stop misbehaving services
- **Process cleanup**: Terminate stuck or runaway processes
- **Security**: Stop potentially malicious processes
- **Maintenance**: Clean up processes during system maintenance
- **Emergency control**: Force termination when normal methods fail

**Alternative termination methods:**
- **kill -9**: Force kill with SIGKILL (cannot be trapped)
- **System shutdown**: System-wide process termination
- **Resource limits**: Process killed for exceeding limits
- **Parent termination**: Child processes terminated when parent dies
- **Session termination**: All processes in session terminated

**Educational value:**
- **Signal limitations**: Not all signals can be trapped
- **System authority**: Operating system has ultimate control
- **Process management**: Understanding how processes can be controlled
- **Administrative tools**: Learning system management utilities
- **Security implications**: How to handle unresponsive processes

**Testing sequence:**
1. **Start highlander**: Run ./7-highlander
2. **Test signal handling**: Try kill <PID> (should show "I am invincible!!!")
3. **Verify continuation**: Process should continue running
4. **Run terminator**: Execute ./67-stop_me_if_you_can
5. **Verify termination**: Highlander process should be completely stopped

**Process state changes:**
- **Running**: Normal execution with signal handling
- **Signal received**: Trap executes, process continues
- **Termination signal**: pkill sends termination signal
- **Process cleanup**: System ensures process terminates
- **Completely stopped**: Process no longer exists

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on processes and signals in Linux systems.
