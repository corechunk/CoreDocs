# 🔵 Milestone 50: Multi-File Projects [PRO]

### 1. Project Orchestration
Large scripts are impossible to maintain. Professional architecture separates configuration, libraries, and logic into discrete files.

```bash
# CONVENTIONAL: Relative Sourcing
source "./lib/api.sh"

# Logic: 'source' performs textual inclusion in the current 
# shell context, allowing you to build modular library suites.
```

### 2. Robust Entry Points
To ensure your script finds its dependencies regardless of where it is executed, you must resolve the absolute root path.

```bash
# EXPLICIT: Root Resolution
readonly ROOT_DIR=$(dirname "$(readlink -f "$0")")
source "$ROOT_DIR/config/settings.conf"

# Logic: 'readlink -f' resolves the physical path on the disk, 
# providing a canonical anchor for relative sourcing.
```
