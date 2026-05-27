# Bash Processes: Functions, Backgrounding, and PID Management

## 1. Backgrounding Functions with `&`
In Bash, when you append `&` to a command or function call, it runs in a **subshell** in the background.

### The Subshell Mechanic
- A function is normally executed in the **current shell environment**.
- Adding `&` forces Bash to **fork** a new process (a subshell).
- This subshell inherits the environment but cannot modify the parent's variables (e.g., setting a variable inside the backgrounded function won't change it in your main script).

## 2. PID Management
- `$$`: The PID of the **current** shell.
- `$!`: The PID of the **last backgrounded** process.

## 3. Practical Example
```bash
my_function() {
    echo "Function started (PID: $$)"
    sleep 5
    echo "Function finished"
}

# Run in background
my_function &
func_pid=$!

echo "Started function with PID: $func_pid"
echo "Current shell PID: $$"

# Wait for it to finish
wait $func_pid
echo "Done"
```
