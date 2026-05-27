# 🔴 Milestone 13: Storage Classes [SYSTEMS]

### 1. External Visibility
Storage classes determine if a variable stays private to the script memory or is shared with external programs (child processes) like `grep`, `awk`, or other scripts.

```bash
# CONVENTIONAL: Script-local
token="123"                # Child programs cannot see this

# EXPLICIT: Environment Export
export API_KEY="X-99"      # Moves variable to Environment Block

# Logic: Exporting copies the variable from the Bash symbol table 
# into the process's Environment Array, which is passed to the 
# Kernel's execve() call when a child starts.
```

### 2. Lifetime Control
Unlike systems languages with `static` keywords, Bash manages lifetime through process persistence. You can simulate static storage or manage cleanup manually.

```bash
# EXPLICIT: Persistence
# Globals defined outside functions persist for the session.

# EXPLICIT: Manual Cleanup
large_data=$(cat giant.txt)
unset large_data           # Immediate deallocation (free())

# Logic: Bash has no Garbage Collector. It is strictly 
# deterministic. 'unset' triggers an immediate free() call in the 
# underlying C code to release the string buffer.
```
