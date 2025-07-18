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

### 5-4_bad_luck_8_is_your_chance
A Bash script that loops from 1 to 10 and displays different messages based on the iteration number using if-elif-else statements.

**Usage:**
```bash
chmod +x ./5-4_bad_luck_8_is_your_chance
./5-4_bad_luck_8_is_your_chance
```

**Expected output:**
```
Best School
Best School
Best School
bad luck
Best School
Best School
Best School
good luck
Best School
Best School
```

**Requirements:**
- Uses a while loop (for and until loops are forbidden)
- Uses if, elif, and else statements for conditional logic
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose
- Displays "bad luck" for the 4th iteration
- Displays "good luck" for the 8th iteration
- Displays "Best School" for all other iterations

**Script structure:**
```bash
#!/usr/bin/env bash
# This script loops from 1 to 10 and displays different messages based on the iteration
i=1
while [ $i -le 10 ]
do
    if [ $i -eq 4 ]
    then
        echo "bad luck"
    elif [ $i -eq 8 ]
    then
        echo "good luck"
    else
        echo "Best School"
    fi
    (($i++))
done
```

**Key concepts:**
- **If-elif-else structure**: Multiple conditional branches in single construct
- **Elif statement**: "else if" - checked only if previous conditions are false
- **Else clause**: Default case when no other conditions match
- **Multiple conditions**: `[ $i -eq 4 ]` and `[ $i -eq 8 ]` for specific iterations
- **Conditional branching**: Different outputs based on loop counter value

**Cultural significance:**
- **Number 4**: Considered unlucky in Chinese culture (sounds like "death")
- **Number 8**: Considered lucky in Chinese culture (sounds like "prosperity")
- **Script logic**: Reflects these cultural beliefs about numbers

**Comparison with previous scripts:**
- **4-if_9_say_hi**: Simple if statement (single condition)
- **5-4_bad_luck_8_is_your_chance**: Complex if-elif-else (multiple conditions)
- **Progression**: From simple loops → single conditions → multiple conditions

### 6-superstitious_numbers
A Bash script that displays numbers from 1 to 20 with additional "bad luck" messages for specific superstitious numbers using a case statement.

**Usage:**
```bash
chmod +x ./6-superstitious_numbers
./6-superstitious_numbers
```

**Expected output:**
```
1
2
3
4
bad luck from China
5
6
7
8
9
bad luck from Japan
10
11
12
13
14
15
16
17
bad luck from Italy
18
19
20
```

**Requirements:**
- Uses a while loop (for and until loops are forbidden)
- Uses a case statement for conditional logic
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose
- Displays numbers 1-20
- Shows "bad luck from China" after number 4
- Shows "bad luck from Japan" after number 9
- Shows "bad luck from Italy" after number 17

**Script structure:**
```bash
#!/usr/bin/env bash
# This script displays numbers from 1 to 20 with bad luck messages on specific iterations
i=1
while [ $i -le 20 ]
do
    echo $i
    case $i in
        4)
            echo "bad luck from China"
            ;;
        9)
            echo "bad luck from Japan"
            ;;
        17)
            echo "bad luck from Italy"
            ;;
    esac
    (($i++))
done
```

**Key concepts:**
- **Case statement**: Alternative to if-elif-else for multiple value matching
- **Case syntax**: `case $variable in pattern) commands ;; esac`
- **Pattern matching**: Exact value matching (4, 9, 17)
- **Double semicolon**: `;;` terminates each case branch
- **Esac**: "case" spelled backwards, closes the case statement
- **No default case**: Only specific patterns have actions

**Cultural significance:**
- **Number 4 (China)**: Sounds like "death" in Chinese (四 sì vs 死 sǐ)
- **Number 9 (Japan)**: Sounds like "suffering" in Japanese (九 ku vs 苦 ku)
- **Number 17 (Italy)**: Considered unlucky in Italian culture (related to Roman numerals XVII)

**Comparison with previous conditional scripts:**
- **4-if_9_say_hi**: Single if condition
- **5-4_bad_luck_8_is_your_chance**: If-elif-else structure
- **6-superstitious_numbers**: Case statement for cleaner multiple value matching
- **Progression**: if → if-elif-else → case (increasing complexity and readability)

### 8-for_ls
A Bash script that displays the content of the current directory in list format, showing only the part of filenames after the first dash (-).

**Usage:**
```bash
chmod +x ./8-for_ls
./8-for_ls
```

**Example:**
If directory contains: `100-read_and_cut`, `1-for_best_school`, `6-superstitious_numbers`

**Expected output:**
```
read_and_cut
for_best_school
superstitious_numbers
```

**Requirements:**
- Uses a for loop (while and until loops are forbidden)
- Displays current directory content in list format
- Shows only the part after the first dash (-)
- Does not display hidden files (starting with .)
- First line: `#!/usr/bin/env bash`
- Second line: Comment explaining the script's purpose

**Script structure:**
```bash
#!/usr/bin/env bash
# This script displays the content of current directory in list format, showing only the part after first dash
for file in *
do
    if [[ ! $file == .* ]]
    then
        echo $file | cut -d'-' -f2-
    fi
done
```

**Key concepts:**
- **For loop with glob**: `for file in *` iterates through all files in current directory
- **Glob pattern**: `*` matches all files (except hidden ones starting with .)
- **Hidden file check**: `[[ ! $file == .* ]]` excludes files starting with dot
- **String manipulation**: `cut -d'-' -f2-` extracts text after first dash
- **Cut command**: `-d'-'` sets dash as delimiter, `-f2-` gets field 2 to end
- **Pipe operation**: `echo $file | cut` passes filename to cut command

**Command breakdown:**
- **`for file in *`**: Loop through all visible files in current directory
- **`[[ ! $file == .* ]]`**: Double bracket test to exclude hidden files
- **`echo $file | cut -d'-' -f2-`**: Extract and display part after first dash
- **`cut -d'-' -f2-`**: Use dash as delimiter, get fields from 2 to end

**Text processing concepts:**
- **Field separation**: Breaking text into parts using delimiters
- **Pipeline**: Chaining commands with | operator
- **Pattern matching**: Using shell patterns like .* for hidden files
- **String extraction**: Getting specific parts of filenames

## About

This is part of the ALX System Engineering & DevOps curriculum, focusing on loops, conditions, and parsing in Bash scripting.
