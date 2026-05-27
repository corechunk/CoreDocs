# 🟢 Milestone 27: Function Basics [CORE]

### 1. Reusable Logic
A function is a named block of code that acts like a miniature script residing in the current shell's memory. Functions allow you to modularize logic without spawning new processes.

```bash
# CONVENTIONAL: Standard syntax
greet() {
    echo "Hello $1"
}

# Logic: Functions must be defined BEFORE they are called. 
# They are stored in the shell's Global Function Table.
```

### 2. Scoped Execution
To write professional-tier scripts, functions should be self-contained and descriptive. The `function` keyword is preferred for readability in large projects.

```bash
# EXPLICIT: Modern syntax & Safety
function greet_user() {
    local name="$1"         # Scope isolation
    echo "Hello $name"
}

# Logic: 'local' creates a temporary entry on the function's 
# Activation Record (Stack), which is automatically popped 
# (destroyed) when the function returns.
```

## Deep-Dive Reference
For advanced argument handling and array expansion:
- [Argument Array ($@)](./array/expansion-manipulation.md)
