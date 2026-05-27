# 🟢 Milestone 25: Iteration - Indefinite [CORE]

### 1. Success-Based Loops
An Indefinite loop runs as long as a command succeeds (`while`) or fails (`until`). This is primarily used for monitoring processes or reading continuous data streams.

```bash
# CONVENTIONAL: Variable check
while [[ $ans != "y" ]]; do
    read -p "Continue? [y/n] " ans
done

# Logic: The loop executes the [[ ]] test before every turn. If 
# it returns non-zero, the loop terminates immediately.
```

### 2. Stream Processing
The "Golden Standard" for processing files or command output line-by-line is the `while read` loop. It is safer and more memory-efficient than `for` loops on file contents.

```bash
# EXPLICIT: Safe File Reading
while IFS= read -r line; do
    echo "Line: $line"
done < "data.txt"

# Logic: 'read' returns success (0) for every line read and 
# failure (non-zero) when it hits EOF (End of File), providing 
# a natural termination for the loop.
```
