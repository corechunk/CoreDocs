# 🟢 Milestone 08: Variables & Constants [CORE]

### 1. Data Storage
A variable is a named pointer to a string of bytes in shell memory. In Bash, assignments are highly sensitive to whitespace; there must be NO SPACES around the assignment operator.

```bash
# CONVENTIONAL: Mutable assignment
user="alice"
count=5

# Logic: Bash creates an entry in its Global Hash Table, 
# dynamically allocating a buffer to hold the string "alice".
```

### 2. Data Protection
Constants are variables that are "Locked" in memory. They provide security for critical paths and ensure that global configuration remains stable.

```bash
# EXPLICIT: Constants (Immutable)
readonly PI=3.14           # C-style constant
declare -r APP_ROOT="/opt" # Attribute-style constant

# EXPLICIT: Global Visibility
export API_KEY="X-123"      # Shared with child processes

# Logic: 'readonly' marks the table entry with a write-protect 
# bit. Any attempt to re-assign triggers a "variable is readonly" 
# trap in the shell.
```
