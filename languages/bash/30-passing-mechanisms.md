# 🟢 Milestone 30: Passing Mechanisms [CORE]

### 1. Pass by Value (Default)
When you hand data to a function, Bash creates a **Copy** of that data. Changes made to the copy do not affect the original variable.

```bash
# CONVENTIONAL: Positional params
function update() {
    local val=$1
    val="new"               # Original variable is UNCHANGED
}

# Logic: Arguments are passed as a list of strings. The local 
# assignment creates a new string buffer in the function scope.
```

### 2. Pass by Reference (Nameref)
Modern Bash (4.3+) allows you to pass a **Link** to a variable name. This allows a function to directly manipulate the memory of a variable outside its scope.

```bash
# EXPLICIT: The Nameref Pattern
function update_global() {
    local -n ref=$1         # 'ref' points to the NAME passed
    ref="new_value"         # Modifies original variable!
}

# USAGE
x="old"
update_global x             # Pass NAME, not $x
echo $x                     # Logic: x is now "new_value"

# Logic: 'declare -n' creates a Symbolic Map in the symbol table. 
# Any access to 'ref' triggers a secondary lookup for the target 
# variable name.
```

### 3. Flag Parsing (The Conveyor Belt)
For professional CLIs, non-positional arguments (flags) are preferred over strictly ordered arguments.

```bash
# EXPLICIT: while/shift pattern
while [[ $# -gt 0 ]]; do
    case "$1" in
        -m|--mode)
            install_mode="$2"
            shift 2 # Consume flag AND value
            ;;
        install|update)
            ACTION="$1"
            shift # Consume only the command
            ;;
        *)
            echo "Unknown: $1"; exit 1 ;;
    esac
done

# Logic: $@ is treated as a stack. 'shift' pops the top item 
# off, moving the next item to index $1.
```

