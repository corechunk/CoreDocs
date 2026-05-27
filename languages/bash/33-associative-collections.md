# 🟢 Milestone 33: Associative Collections [CORE]

### 1. Key-Value Maps
An associative collection (Map/Dictionary) is a hash table where keys are strings instead of numbers. This is the primary tool for configuration and data lookup in Bash.

```bash
# EXPLICIT: Mandatory Declaration
declare -A config           # MUST be declared as -A

# ASSIGNMENT
config=([port]=8080 [host]="localhost")
config[theme]="dark"

# Logic: Bash runs a hashing algorithm on the string key to 
# determine the memory bucket for the value, providing O(1) 
# lookup performance.
```

### 2. Advanced Inspection
Associative arrays allow you to iterate over keys, values, or both. This is essential for building dynamic configuration loaders.

```bash
# EXPLICIT: Key/Value Iteration
for key in "${!config[@]}"; do
    echo "Key: $key | Value: ${config[$key]}"
done

# Logic: The '!' marker tells the expansion engine to return 
# the index list (keys) rather than the contents of the buckets.
```
