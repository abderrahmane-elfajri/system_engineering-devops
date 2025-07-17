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
- **For loop**: More compact, ideal when you know exact number of iterations
- **While loop**: More flexible, continues as long as condition is true
- **Both**: Achieve the same result but with different syntax and control flow

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on loops, conditions, and parsing in Bash scripting.
