# 🟢 Milestone 12: Scope & Lifetime [CORE]

### 1. Visibility Rules
Scope determines where a variable is "seen." In Bash, the default behavior is extreme: every variable is **Global** to the current shell process.

```bash
# CONVENTIONAL: Global pollution
x=10
function set_x() { x=20; }
set_x
echo $x                    # Logic: Output is 20 (Global overwritten)

# Logic: Variables are stored in a single process-wide hash table. 
# Functions share this same memory space by default.
```

### 2. Variable Isolation
To write safe, reusable scripts, you must explicitly manage scope. This prevents functions from accidentally corrupting global state or each other.

```bash
# EXPLICIT: Local Function Scope
function my_func() {
    local temp="secret"    # Isolated to this function
}

# EXPLICIT: Subshell Isolation
x=10
( x=20 )                   # Forked child process
echo $x                    # Logic: Still 10 (Parent is protected)

# Logic: 'local' creates a temporary entry on the function's 
# Activation Record (Stack). Subshells '( )' trigger a fork(), 
# creating an entire copy of the process memory.
```
