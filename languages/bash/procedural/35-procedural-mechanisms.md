# 🔵 Milestone 35: Procedural Mechanisms [PRO]

### 1. Modular Scripts
Modularity is the act of splitting logic into specialized files (libraries). In Bash, the `source` command is the primary mechanism for procedural orchestration.

```bash
# CONVENTIONAL: Execution
./lib/utils.sh              # Logic: Runs in child process (NO sharing)

# EXPLICIT: Textual Inclusion (Import)
source "./lib/utils.sh"      # Logic: Runs in CURRENT process (Shares all)

# Logic: 'source' (or '.') tells the Bash parser to open the 
# target file and interpret its content as if it were typed 
# directly into the current line.
```

### 2. Reliable Discovery
To ensure your script can find its libraries regardless of where it is called from, you must resolve the absolute path of the script's origin.

```bash
# EXPLICIT: Relative Orchestration
readonly LIB_DIR="$(dirname "$(readlink -f "$0")")/lib"
source "${LIB_DIR}/core.sh"

# Logic: 'readlink -f' resolves symlinks and relative paths to 
# a canonical absolute path on the disk.
```
