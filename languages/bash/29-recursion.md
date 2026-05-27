# 🟢 Milestone 29: Recursion [CORE]

### 1. Self-Reference
Recursion is when a function calls itself to solve a problem by breaking it into smaller sub-tasks. While possible in Bash, it is subject to strict memory and process limits.

```bash
# CONVENTIONAL: Numeric recursion
function factorial() {
    local n=$1
    if (( n <= 1 )); then
        echo 1
    else
        local prev=$(factorial $(( n - 1 )))
        echo $(( n * prev ))
    fi
}

# Logic: Every call pushes a new layer of shell memory (Activation 
# Frame) onto the internal stack.
```

### 2. Recursion Limits
Bash is not optimized for deep recursion (no tail-call optimization). You must manually monitor depth to prevent script crashes or "Stack Overflow" equivalents.

```bash
# EXPLICIT: Depth Guard
function recurse() {
    local depth=$1
    if (( depth > 100 )); then
        echo "Error: Max depth reached" >&2
        return 1
    fi
    recurse $(( depth + 1 ))
}

# Logic: Recursion depth is tracked by the BASH_SUBSHELL or 
# manual counters. Exceeding limits triggers a segmentation 
# fault in the shell's C-engine.
```
