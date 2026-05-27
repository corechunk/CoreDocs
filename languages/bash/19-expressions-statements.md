# 🟢 Milestone 19: Expressions vs Statements [CORE]

### 1. Functional Actions (Statements)
A Statement is a command that performs an action (e.g., creating a directory). In Bash, every statement results in a status code in the CPU's register.

```bash
# CONVENTIONAL: Simple action
mkdir "/tmp/backup"

# Logic: The command executes and populates the '$?' variable 
# with the success/failure code from the Kernel.
```

### 2. Evaluative Logic (Expressions)
An Expression is logic that produces a boolean-like result. In Bash, expressions are often used to decide whether to execute a following statement via "Short-circuiting."

```bash
# EXPLICIT: Logical Chain
[[ -d "/tmp" ]] && echo "Exists" || exit 1

# Logic: Bash treats '&&' and '||' as flow control. It only 
# executes the next statement if the current status matches the 
# operator's requirement (0 for &&, non-zero for ||).
```
