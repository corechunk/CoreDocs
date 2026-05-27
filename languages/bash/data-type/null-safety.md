# 🟢 Bash: Null Safety & Default Values [CORE]

### 1. Default Value Substitution
Handling variables that might be empty or unset is critical for script stability.

```bash
# CONVENTIONAL: If-check for empty
if [ -z "$user" ]; then
    user="guest"
fi

# Logic: Procedural check for string length.
```

```bash
# EXPLICIT: Native Null-Coalescing
echo "${user:-guest}"      # Logic: guest (If unset/empty)
echo "${user:=guest}"      # Logic: sets user="guest" if empty

# Logic: The ':' prefix ensures the check applies to BOTH unset 
# variables AND empty strings ("").
```

### 2. Mandatory Variable Checks
Ensuring a variable exists before proceeding to destructive operations.

```bash
# CONVENTIONAL: Manual exit
if [ -z "$TARGET_DIR" ]; then
    echo "Error: TARGET_DIR not set"
    exit 1
fi
rm -rf "$TARGET_DIR"/*

# Logic: Manual verification of state.
```

```bash
# EXPLICIT: Assertion Expansion
rm -rf "${TARGET_DIR:?Error: Var not set}"/*

# Logic: The ':?' syntax triggers a shell-level abortion and 
# prints the message to stderr if the variable is null, 
# preventing accidental 'rm -rf /*' scenarios.
```

# The Logic Bridge
// Logic: Parameter expansion "Coalescing" happens entirely within the shell's parser. It allows for declarative error handling and state initialization, reducing the "Surface Area" for bugs caused by unexpected empty strings.
