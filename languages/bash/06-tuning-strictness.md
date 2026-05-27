# 🔵 Milestone 06: Tuning & Strictness [PRO]

### 1. The "Lazy" Default
By default, Bash is optimized for interactive speed, not script safety. It will continue running even if a critical command (like `cd`) fails, leading to the "Snowball Effect" where one failure corrupts future operations.

```bash
# CONVENTIONAL: Loose execution
cd /nonexistent_dir
rm -rf *                   # WARNING: Deletes files in WRONG dir

# Logic: Without strictness, the shell ignores the non-zero exit 
# status of the 'cd' command and blindly executes the next line.
```

### 2. The "Unofficially-Official" Safe Mode
Tuning strictness enables "Guardrails" that force the shell to behave like a modern programming language, catching logical errors during the build process.

```bash
# EXPLICIT: The Golden Set
set -e                     # Fail-Fast: Exit on first error
set -u                     # Unbound Check: Error on unset variables
set -o pipefail            # Pipe Safety: Check ALL commands in a pipe

# BASH 4.0+ ENHANCEMENT
shopt -s inherit_errexit   # Pass -e into subshells ()

# Logic: These flags modify the Shell's internal Signal Table. 
# When 'set -e' is on, the shell internally wraps every command 
# in a check for the CPU's Status Register.
```
