# 🔵 Milestone 14: Native Strings [PRO]

### 1. High-Speed Slicing
Bash can manipulate strings directly in memory without calling external binaries. This "Pure Bash" approach is orders of magnitude faster because it avoids process forking.

```bash
# CONVENTIONAL: Slow external call
echo "Hello" | cut -c 1-3

# EXPLICIT: Fast Native Slicing
str="Hello World"
echo "${str:0:5}"           # Logic: Start 0, Length 5 -> "Hello"
echo "${str: -5}"           # Logic: Last 5 characters

# Logic: The shell's internal C-engine performs pointer 
# arithmetic on the string buffer to extract slices instantly.
```

### 2. Search & Replace
Bash provides built-in operators for pattern-based string transformation, ideal for renaming files or sanitizing paths.

```bash
# EXPLICIT: Pattern Replacement
path="/var/log/app.log"
echo "${path/log/run}"      # Replace FIRST instance
echo "${path//log/run}"     # Replace ALL instances

# Logic: Bash uses its internal globbing engine to find matches 
# and re-constructs the string in a new memory buffer.
```
