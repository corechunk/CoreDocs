# 🟢 Milestone 49: Error Handling [CORE]

### 1. Manual Checks
Error handling is the "Safety Net" of a script. Since Bash has no `try/catch`, you must manually verify the outcome of critical operations.

```bash
# CONVENTIONAL: Status Tracking
cp source.sh backup.sh
if (( $? != 0 )); then
    echo "Error: Backup failed" >&2
    exit 1
fi

# Logic: The exit status register must be checked immediately.
```

### 2. Global Guardrails
For production scripts, use a global "Trap" pattern to handle any unexpected failure without manual checks on every line.

```bash
# EXPLICIT: The Error Trap
set -e                      # Fail-fast mode
trap 'echo "Error on line $LINENO"' ERR

# Logic: The 'ERR' signal is triggered by the shell whenever a 
# command returns non-zero while 'set -e' is active.
```
