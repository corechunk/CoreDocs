# 🟢 Milestone 28: Return Types [CORE]

### 1. Status Returns
Bash functions **cannot return data** (like strings or objects) directly. They can only return an **Exit Status** (a number from 0 to 255).

```bash
# EXPLICIT: Success/Failure Logic
function is_active() {
    [[ $STATUS == "RUNNING" ]] && return 0 || return 1
}

# Logic: The 'return' keyword only populates the shell's 
# internal '$?' variable for immediate logical checking.
```

### 2. Data "Returns" (Stdout)
To "Return" text or data structures, you must print them to the standard output and capture that stream using command substitution.

```bash
# EXPLICIT: Data Return Pattern
function get_config_val() {
    echo "api_v1_live"      # Result printed to stdout
}

# CAPTURE
result=$(get_config_val)

# Logic: Command substitution $( ) works by capturing the 
# Standard Output Stream (FD 1) of the function execution context.
```
