# 🟢 Milestone 05: Keywords & Standards [CORE]

### 1. Command Hierarchy
Not every command in Bash is a "Program" on your disk. Bash follows a specific lookup order to decide how to execute a word: **Keyword $\to$ Built-in $\to$ External**.

```bash
# CONVENTIONAL: General execution
if [[ -d /tmp ]]; then cd /tmp; ls; fi

# EXPLICIT: Resolving Command Source
type if                    # "if is a shell keyword" (Shell Grammar)
type cd                    # "cd is a shell builtin" (Internal to Bash)
type ls                    # "ls is /usr/bin/ls" (External Binary)

# Logic: Keywords control the parser. Built-ins run in the 
# current shell RAM. Externals require spawning a new process.
```

### 2. Standards & Portability
Bash has different "Modes" (like POSIX mode) that change its behavior to match older shell standards (like Sh or Dash).

```bash
# EXPLICIT: POSIX Enforcement
# bash --posix             # Start shell in strict POSIX mode

# Logic: Bash attempts to balance modern "Power" with legacy 
# "Compatibility." Standards mode disables Bash-only features 
# like [[ ]] or arrays.
```
