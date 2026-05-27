# 🔵 Milestone 31: Closures & Lambdas [PRO]

### 1. Lambda Simulation
Bash has no native syntax for anonymous functions (lambdas). However, you can simulate them by passing strings of code and evaluating them dynamically.

```bash
# EXPLICIT: Dynamic Execution
function map() {
    local code=$1; shift
    for item in "$@"; do
        eval "$code \"$item\""
    done
}

map 'echo "Item:"' "a" "b"

# Logic: 'eval' forces the shell to run its Parser and Lexer on 
# a string at runtime, treating it as functional code.
```

### 2. Closure Simulation
A closure is a function that "Closes over" the variables of its parent. In Bash, we simulate this using subshells to "Freeze" the current environment state.

```bash
# EXPLICIT: Scoped Snapshot
x=10
generate_callback() {
    ( echo "Frozen X: $x" ) # Snapshot at time of creation
}

# Logic: Because subshells ( ) perform a fork(), they receive a 
# complete copy of all parent variables at that specific 
# moment in time.
```
