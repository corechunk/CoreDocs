# 🔴 Milestone 16: Syntactic Automation [SYSTEMS]

### 1. Macro Simulation (Aliases)
Automation in Bash often begins with Aliases—simple word replacements that act like preprocessor macros. They are ideal for interactive shortcuts but have strict limitations in scripts.

```bash
# CONVENTIONAL: Interactive shortcut
alias ll='ls -la'

# EXPLICIT: Scripted Expansion
shopt -s expand_aliases     # Aliases are DISABLED in scripts by default
alias log='echo "[$(date)]"'

# Logic: During the Parsing Phase, Bash checks the first word of 
# every command against the Alias Hash Table and textually 
# replaces it before the Lexer continues.
```

### 2. Functional Shortcuts
Functions are the primary tool for automation in Bash scripts. Unlike aliases, they support parameters and complex logic, acting as "First-class commands" within the shell environment.

```bash
# EXPLICIT: Automated Wrapper
function backup() {
    local target=$1
    tar -czf "${target}.tar.gz" "$target"
}

# Logic: Functions are stored in the Global Function Table. 
# Calling a function jumps execution to that memory address 
# within the current process context.
```
