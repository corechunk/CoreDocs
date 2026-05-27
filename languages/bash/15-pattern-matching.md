# 🔵 Milestone 15: Pattern Matching [PRO]

### 1. Globbing (The Basics)
Pattern matching checks if a string conforms to a specific "Shape." Globbing is the simplest form, used primarily for file discovery.

```bash
# CONVENTIONAL: Basic wildcards
ls *.txt                    # Match any filename ending in .txt

# EXPLICIT: Extended Globs
shopt -s extglob            # Enable advanced features
if [[ $file == *.@(jpg|png) ]]; then 
    echo "Image found"
fi

# Logic: The shell's Glob Engine scans the directory or string 
# using simple state-machine matching (?, *, [ ]).
```

### 2. Regex (The Heavy Hitter)
For complex validation (like verifying an IP address or email), Bash provides native Regular Expression matching using the same engine as many systems languages.

```bash
# EXPLICIT: Native Regex
input="192.168.1.1"
if [[ $input =~ ^[0-9]{1,3}\.[0-9]{1,3} ]]; then
    echo "Valid prefix"
fi

# Logic: Bash uses the system's regex.h library. Match results 
# for capturing groups are stored in the BASH_REMATCH array.
```
