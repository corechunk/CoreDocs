# 🟢 Bash: Argument Handling & Array Expansion [CORE]

### 1. The Argument Array ($@)
When handling multiple inputs in a function or script, `$@` represents all positional parameters as separate words. Using it inside double quotes `"$@"` is the only safe way to preserve spaces in arguments.

```bash
# CONVENTIONAL: Simple iteration
function list_args() {
    for arg in $@; do
        echo "Arg: $arg"
    done
}

# Logic: Without quotes, an argument like "Hello World" is 
# split into two separate items by the shell's IFS engine.
```

```bash
# EXPLICIT: Safe Expansion
function list_args_safe() {
    for arg in "$@"; do
        echo "Arg: $arg"
    done
}

# USAGE: list_args_safe "A B" "C"
# Logic: "$@" ensures the Kernel sees "A B" as a single 
# pointer in the argument array, preventing word-splitting.
```

### 2. Mass Array Manipulation (${arr[@]})
The `@` symbol is a "Wildcard" for collection indices. It allows you to perform operations on every element of an array simultaneously without a loop.

```bash
# CONVENTIONAL: Loop-based manipulation
files=(data.txt logs.txt)
for f in "${files[@]}"; do
    mv "$f" "${f%.txt}.bak"
done

# Logic: Standard procedural approach to renaming.
```

```bash
# EXPLICIT: Direct Expansion Manipulation
files=(data.txt logs.txt)
echo "${files[@]%.txt}"     # Logic: data logs (removes suffix)
echo "${files[@]^^}"        # Logic: DATA.TXT LOGS.TXT (uppercase)

# Logic: Bash's expansion engine applies the pattern filter 
# to every string pointer in the array buffer before outputting 
# the resulting stream.
```

# The Logic Bridge
// Logic: The `@` expansion works by duplicating the expansion logic for every member of the array. It is fundamentally different from `*` which collapses all members into a single string. In the internal C implementation, `"$@"` is handled by a specialized loop that bypasses the standard string-collapse logic.
