# 🟢 Milestone 11: Interpolation [CORE]

### 1. Variable Substitution
Interpolation is the act of replacing a variable placeholder (like `$VAR`) with its actual content. In Bash, this happens during the "Expansion" phase of command processing.

```bash
# CONVENTIONAL: Simple expansion
user="Alice"
echo "Hello $user"         # Hello Alice

# EXPLICIT: Ambiguity prevention
echo "${user}_backup"      # Prevents looking for 'user_backup' var

# Logic: Bash scans the string for the '$' marker, lookups the 
# name in the symbol table, and replaces the marker with the 
# literal bytes of the value.
```

### 2. Advanced Fallbacks
Bash interpolation supports logic for handling unset or null variables. This is the "Pro" way to provide default configuration values without using `if` statements.

```bash
# EXPLICIT: Default Values
echo "${user:-Guest}"      # Use "Guest" if user is unset/null
echo "${user:=Admin}"      # Set user to "Admin" if unset, then return it

# EXPLICIT: Error on Missing
: "${user:?Error: User not defined}" # Exit script if unset

# Logic: These operators are handled by the shell's internal 
# Expansion Engine, allowing for conditional data injection 
# before the command is executed.
```
