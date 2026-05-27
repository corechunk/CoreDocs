# 🔵 Milestone 53: Standard Library [PRO]

### 1. The Built-in Toolbox
Bash doesn't have a single `stdlib` file. Its "Standard Library" is the collection of built-ins and core utilities that are guaranteed to exist on a POSIX-compliant system.

```bash
# CONVENTIONAL: Core Utilities
ls, cp, mv, rm, mkdir      # File Ops
grep, sed, awk, cut, tr    # Text Ops
env, export, set, alias    # Environment Ops

# Logic: These tools are the building blocks of the shell 
# language, providing the "Functional Muscle" for script logic.
```

### 2. Shell Built-ins
Built-ins are commands that live *inside* the Bash binary. They are faster and have direct access to shell memory.

```bash
# EXPLICIT: Using Built-ins
type cd                    # "cd is a shell builtin"
help echo                  # Documentation for built-ins

# Logic: Built-ins run in the shell's memory space, bypassing 
# the Kernel's exec() overhead.
```
