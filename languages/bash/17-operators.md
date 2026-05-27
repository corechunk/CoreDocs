# 🟢 Milestone 17: Operators [CORE]

### 1. The Engine Choice
Operators are the symbols that perform actions on data. In Bash, you must choose the right "Evaluation Engine" based on the data type.

```bash
# CONVENTIONAL: String comparison
if [[ $a == $b ]]; then :; fi

# Logic: [[ ]] triggers the shell's Logical Test Engine, which 
# treats operands as strings unless a specific operator 
# (like -eq) is used.
```

### 2. Specialized Operators
Bash provides two distinct sets of operators: one for C-style math and one for high-level logical tests.

```bash
# EXPLICIT: Arithmetic Operators (Inside (( )))
# Math: +, -, *, /, % | Bitwise: <<, >>, &, |, ^
(( res = (5 + 2) << 1 ))    # Logic: 7 shifted left -> 14

# EXPLICIT: Logical/File Operators (Inside [[ ]])
# Logic: &&, ||, ! | File: -f (file), -d (dir), -z (empty)
if [[ -f "/etc/passwd" && ! -z $USER ]]; then :; fi

# Logic: Arithmetic operators work on binary representations. 
# Logical operators work on string attributes and file metadata.
```

## Deep-Dive Reference
For low-level bit manipulation and math:
- [Bitwise Operators](./operator/bitwise.md)
