# 🟢 Bash: Floating Point (The Limitation) [CORE]

### 1. The Integer Boundary
Bash is strictly an Integer-based language. It cannot natively process decimal numbers (floats) in its arithmetic engine.

```bash
# CONVENTIONAL: The Error
# x=$(( 10.5 + 2 ))         # Logic: syntax error: invalid arithmetic operator
```

### 2. The External Bridge (bc)
To perform decimal math, you must hand the data to an external processor like `bc` (Binary Calculator).

```bash
# CONVENTIONAL: Simple division
echo "10 / 3" | bc          # Logic: 3 (Default scale is 0)

# EXPLICIT: Precision Math
val=$(echo "scale=2; 10 / 3" | bc)
echo $val                   # Logic: 3.33

# Logic: Since Bash cannot store the float, the result is 
# captured as a STRING. Any subsequent math must again use 
# an external tool.
```

# The Logic Bridge
// Logic: Bash's internal arithmetic is performed using the `long` type in C. Decimal support was intentionally excluded from the shell's core to keep it lightweight and focused on process management. High-performance scripts should use `awk` or `python` for math-intensive logic.
