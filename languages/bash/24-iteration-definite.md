# 🟢 Milestone 24: Iteration - Definite [CORE]

### 1. List Iteration
A Definite loop runs a specific number of times based on a provided list of items. In Bash, `for` loops iterate over **Words** separated by whitespace.

```bash
# CONVENTIONAL: Literal list
for fruit in apple banana cherry; do
    echo "I like $fruit"
done

# Logic: The expansion engine replaces 'apple banana cherry' with 
# three separate tokens before the loop begins.
```

### 2. Structured Iteration
For arrays or numeric ranges, you must use specific expansion rules or C-style syntax to avoid word-splitting bugs and ensure precise control.

```bash
# EXPLICIT: Array Iteration (Safe)
declare -a list=("Item 1" "Item 2")
for item in "${list[@]}"; do    # Logic: Always quote for safety
    echo "Processing $item"
done

# EXPLICIT: C-Style Numeric Loop
for (( i=0; i<10; i++ )); do
    echo "Count: $i"
done

# Logic: "${arr[@]}" expands to a set of perfectly isolated 
# strings. C-style loops use the arithmetic engine for counting.
```
