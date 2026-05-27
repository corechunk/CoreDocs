# 🟢 Milestone 32: Sequential Collections [CORE]

### 1. The Indexed Array
A sequential collection is a list of values indexed by integers (0, 1, 2...). In Bash, arrays are "Sparse," meaning you can assign value to index 100 without filling indices 0-99.

```bash
# CONVENTIONAL: Simple list
fruits=(apple banana cherry)
echo "${fruits[1]}"         # Logic: banana

# Logic: Sequential arrays are stored internally as a linked-list 
# of string pointers indexed by integer keys.
```

### 2. High-Performance Loading
For large data sets, Bash provides optimized built-ins that bypass the slow word-splitting engine to load file contents directly into memory arrays.

```bash
# EXPLICIT: Declaration & Loading
declare -a log_lines
mapfile -t log_lines < access.log

# SAFE ITERATION
for line in "${log_lines[@]}"; do
    echo "Processing: $line"
done

# Logic: 'mapfile' (readarray) uses an optimized C-loop to read 
# bytes into the array structure, providing significant speed 
# gains over 'while read' for static data.
```

## Deep-Dive Reference
For advanced manipulation and expansion techniques:
- [Expansion & Manipulation](./array/expansion-manipulation.md)
