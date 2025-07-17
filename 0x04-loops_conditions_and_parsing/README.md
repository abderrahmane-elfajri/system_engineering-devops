# 0x04. Loops, conditions and parsing

This directory contains scripts that demonstrate loops, conditions, and parsing in Bash scripting.

## Files

### 1-for_best_school
A Bash script that displays "Best School" exactly 10 times using a for loop.

**Usage:**
```bash
chmod +x ./1-for_best_school
./1-for_best_school
```

**Expected output:**
```
Best School
Best School
Best School
Best School
Best School
Best School
Best School
Best School
Best School
Best School
```

**Requirements:**
- Uses a for loop (while and until loops are forbidden)
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose
- Displays "Best School" exactly 10 times

**Script structure:**
```bash
#!/usr/bin/env bash
# This script is displaying "Best School" 10 times
for ((i=1; i<=10; i++))
do
    echo "Best School"
done
```

**Key concepts:**
- **For loop syntax**: `for ((initialization; condition; increment))`
- **Loop body**: Commands executed in each iteration
- **Echo command**: Outputs text to standard output
- **Loop counter**: Variable `i` tracks iterations from 1 to 10

### 2-while_best_school
A Bash script that displays "Best School" exactly 10 times using a while loop.

**Usage:**
```bash
chmod +x ./2-while_best_school
./2-while_best_school
```

**Expected output:**
```
Best School
Best School
Best School
Best School
Best School
Best School
Best School
Best School
Best School
Best School
```

**Requirements:**
- Uses a while loop (for and until loops are forbidden)
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose
- Displays "Best School" exactly 10 times

**Script structure:**
```bash
#!/usr/bin/env bash
# This script is displaying "Best School" 10 times
i=1
while [ $i -le 10 ]
do
    echo "Best School"
    ((i++))
done
```

**Key concepts:**
- **While loop syntax**: `while [ condition ]`
- **Test condition**: `[ $i -le 10 ]` checks if i is less than or equal to 10
- **Loop initialization**: Variable `i` starts at 1
- **Loop increment**: `((i++))` increases the counter by 1 each iteration
- **Loop body**: Commands executed while condition is true

**Comparison with for loop:**
- For loop: Counter and condition built into loop statement
- While loop: Requires manual initialization and increment of counter
- While loop: More flexible for complex conditions

### 3-until_best_school
A Bash script that displays "Best School" exactly 10 times using an until loop.

**Usage:**
```bash
chmod +x ./3-until_best_school
./3-until_best_school
```

**Expected output:**
```
Best School
Best School
Best School
Best School
Best School
Best School
Best School
Best School
Best School
Best School
```

**Requirements:**
- Uses an until loop (for and while loops are forbidden)
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose
- Displays "Best School" exactly 10 times

**Script structure:**
```bash
#!/usr/bin/env bash
# This script is displaying "Best School" 10 times
i=1
until [ $i -gt 10 ]
do
    echo "Best School"
    ((i++))
done
```

**Key concepts:**
- **Until loop syntax**: `until [ condition ]`
- **Test condition**: `[ $i -gt 10 ]` checks if i is greater than 10
- **Loop logic**: Executes until condition becomes true (opposite of while)
- **Loop initialization**: Variable `i` starts at 1
- **Loop increment**: `((i++))` increases the counter by 1 each iteration
- **Loop termination**: Stops when i becomes greater than 10

**Comparison with while loop:**
- While loop: Continues while condition is true
- Until loop: Continues until condition becomes true
- Until loop: Uses opposite logic (loop while NOT condition)
- Both require manual counter initialization and increment

**Loop types summary:**
- **For loop**: Best for known number of iterations with simple counter
- **While loop**: Best when you want to continue while something is true
- **Until loop**: Best when you want to continue until something becomes true

### 4-if_9_say_hi
A Bash script that displays "Best School" 10 times, but on the 9th iteration it also displays "Hi" on a new line.

**Usage:**
```bash
chmod +x ./4-if_9_say_hi
./4-if_9_say_hi
```

**Expected output:**
```
Best School
Best School
Best School
Best School
Best School
Best School
Best School
Best School
Best School
Hi
Best School
```

**Requirements:**
- Uses a while loop (for and until loops are forbidden)
- Uses an if statement to check for the 9th iteration
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose
- Displays "Best School" exactly 10 times
- On the 9th iteration, displays "Hi" after "Best School"

**Script structure:**
```bash
#!/usr/bin/env bash
# This script displays "Best School" 10 times, but on the 9th iteration it also displays "Hi"
i=1
while [ $i -le 10 ]
do
    echo "Best School"
    if [ $i -eq 9 ]
    then
        echo "Hi"
    fi
    ((i++))
done
```

**Key concepts:**
- **Combining loops and conditionals**: Using if statement inside while loop
- **Conditional logic**: `[ $i -eq 9 ]` checks if counter equals 9
- **If statement syntax**: `if [ condition ]; then ... fi`
- **Sequential execution**: "Best School" prints first, then condition is checked
- **Indentation**: Proper nesting with 4 spaces for loop body, 8 spaces for if body

**Comparison with previous scripts:**
- **1-for_best_school**: Simple for loop, no conditions
- **2-while_best_school**: Simple while loop, no conditions  
- **3-until_best_school**: Simple until loop, no conditions
- **4-if_9_say_hi**: While loop + conditional logic for dynamic behavior

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on loops, conditions, and parsing in Bash scripting.
