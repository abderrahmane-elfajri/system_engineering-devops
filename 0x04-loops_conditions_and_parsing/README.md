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

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on loops, conditions, and parsing in Bash scripting.
