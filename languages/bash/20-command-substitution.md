# 🔵 Milestone 20: Command Substitution [PRO]

### 1. Output Capture
Command substitution is the act of running a program and capturing its text output into a variable. This is the primary way Bash scripts process data from external tools.

```bash
# CONVENTIONAL: Captured status
now=$(date)
echo "Current time is $now"

# Logic: Bash forks a subshell, connects its stdout to a pipe, 
# and reads the data into the parent's memory buffer.
```

### 2. Nesting & Performance
Modern Bash allows for nested substitutions, providing a way to build complex data structures from multiple command outputs in a single line.

```bash
# EXPLICIT: Nested Capture
# 1. List files 2. Count them 3. Prepend metadata
info="Count: $(ls -1 | wc -l) (at $(date +%H:%M))"

# Logic: Nesting triggers multiple forks. Each internal $( ) 
# must complete and pass its bytes to the enclosing expansion 
# engine before the final command is constructed.
```
