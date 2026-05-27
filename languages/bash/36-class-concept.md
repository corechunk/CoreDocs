# 🟢 Milestone 36: Class Concept [CORE]

### 1. Dynamic Instances
A Class is a blueprint for objects. In Bash, we simulate this by generating **Unique Associative Arrays** for every "Instance" of the class at runtime.

```bash
# EXPLICIT: The Constructor Pattern
function User.new() {
    local id=$1; local name=$2
    local var_name="user_$id"
    
    declare -g -A "$var_name" # Logic: Create GLOBAL instance
    local -n self="$var_name"
    self[id]=$id; self[name]="$name"
    
    echo "$var_name"          # Return instance HANDLE
}

# Logic: This uses Metaprogramming to inject new entries into 
# the shell's global symbol table dynamically.
```

### 2. Object Access
To use the "Object," you capture its handle and bind it to a local nameref for easy field access.

```bash
# USAGE
handle=$(User.new 42 "Bob")
local -n bob="$handle"
echo "${bob[name]}"         # Logic: Bob
```
