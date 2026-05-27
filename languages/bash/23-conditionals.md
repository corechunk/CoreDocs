# 🟢 Milestone 23: Conditionals [CORE]

### 1. Simple Branching (if)
Conditionals are decision points that direct execution based on command success. The `if` statement is the primary tool for binary (Yes/No) logic.

```bash
# CONVENTIONAL: File check
if [[ -f "config.sh" ]]; then
    source "config.sh"
fi

# Logic: 'if' executes the [[ ]] keyword. If [[ ]] returns 0 
# (success), the 'then' block is executed.
```

### 2. Pattern Branching (case)
The `case` statement is the "Switch" equivalent in Bash. It is optimized for matching a single string against multiple patterns (globbing), making it significantly cleaner than nested `elif` blocks.

```bash
# EXPLICIT: Multi-branch Match
case "$1" in
    start|run)
        ./app --daemon
        ;;
    stop)
        kill $(cat pid.file)
        ;;
    *)
        echo "Usage: $0 {start|stop}"
        exit 1
        ;;
esac

# Logic: 'case' uses a jump-table logic internally. It performs 
# a Lexical Match of the input string against each pattern until 
# it finds a success or hits the '*' default.
```
