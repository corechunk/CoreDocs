# 🟢 Bash: Parameter Expansion [CORE]

### 1. Simple Variable Access
The standard way to retrieve a variable's value.

```bash
# CONVENTIONAL: Shorthand access
name="Corechunk"
echo $name

# Logic: The '$' triggers a lookup in the local scope hash table.
```

```bash
# EXPLICIT: Braced Expansion
name="Corechunk"
echo "${name}"

# Logic: Braces '{}' define the boundary of the variable name, 
# preventing ambiguity (e.g., "${name}_v2" vs "$name_v2").
```

### 2. Advanced Slicing & Substitution
Parameter expansion allows you to modify the string during the retrieval process without changing the original variable.

```bash
# CONVENTIONAL: External tool (sed/cut)
path="/home/user/file.txt"
filename=$(basename "$path")

# Logic: Spawns a subshell and executes an external binary.
```

```bash
# EXPLICIT: Native String Logic
path="/home/user/file.txt"
echo "${path##*/}"         # Logic: file.txt (Remove longest prefix)
echo "${path%/*}"          # Logic: /home/user (Remove shortest suffix)
echo "${path/user/root}"   # Logic: /home/root/file.txt (Replace)

# Logic: Native expansion is performed inside the shell's memory 
# space, making it thousands of times faster than calling 
# external tools like 'basename' or 'dirname'.
```

# The Logic Bridge
// Logic: Parameter expansion is the most powerful "Native" feature of Bash. It operates directly on the string pointers in the shell's memory, allowing for complex parsing and manipulation without the overhead of process creation.
