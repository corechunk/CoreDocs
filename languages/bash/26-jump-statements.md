# 🔵 Milestone 26: Jump Statements [PRO]

### 1. Loop Control
Jump statements redirect the flow of execution within loops. They allow you to skip iterations or break out of nested structures when a specific condition is met.

```bash
# EXPLICIT: Skip & Terminate
for i in {1..10}; do
    if (( i % 2 == 0 )); then continue; fi # Skip evens
    if (( i > 7 )); then break; fi          # Stop at 7
    echo "Odd: $i"
done

# Logic: 'continue' jumps back to the loop header; 'break' jumps 
# to the memory address immediately following the 'done' keyword.
```

### 2. Script Termination
To stop execution of a function or the entire script, Bash provides `return` and `exit`. These pass a status code back to the parent environment.

```bash
# EXPLICIT: Global Exit
if [[ -z $API_KEY ]]; then
    echo "Error: Missing key" >&2
    exit 1 # Terminate entire process with error status
fi

# Logic: 'exit' triggers the Kernel's _exit() call, passing the 
# argument to the parent process's Wait Status register.
```
