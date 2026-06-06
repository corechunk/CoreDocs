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

### 3. Trims and Strips (Parameter Expansion)
Bash provides surgical tools to "cut" strings from either the start or the end based on patterns.

#### The "Keyboard Position" Rule
- **`#`** (Shift+3) is on the **LEFT**: It removes from the **START** (left).
- **`%`** (Shift+5) is on the **RIGHT**: It removes from the **END** (right).

| Operator | Action | Greediness | Logical Description |
| :--- | :--- | :--- | :--- |
| `${var#pattern}` | Start -> | Shortest | Remove the smallest match from the left. |
| `${var##pattern}`| Start -> | **Longest** | **Greedy**: Remove the largest match from the left. |
| `${var%pattern}` | <- End | Shortest | Remove the smallest match from the right. |
| `${var%%pattern}`| <- End | **Longest** | **Greedy**: Remove the largest match from the right. |

#### Visualizing the "Eat" Direction (`*` as Discard)
The `*` acts as the "garbage" you want to throw away. Its position relative to the delimiter determines the result.

```bash
VAR="APPLE | BANANA | CHERRY"

# 1. DISCARD THE START (#) - * comes BEFORE delimiter
echo "${VAR#*|}"     # Result: " BANANA | CHERRY" (Ate first pipe and left)

# 2. DISCARD THE END (%) - * comes AFTER delimiter
echo "${VAR%|*}"     # Result: "APPLE | BANANA " (Ate last pipe and right)

# 3. GREEDY STRIP (##) - Eat everything to the absolute LAST delimiter
echo "${VAR##*|}"    # Result: " CHERRY" (Ate everything up to last pipe)
```

#### Surgical "Edge" Removal (No Wildcard)
If you omit the `*`, Bash only removes the match if it is at the **absolute tip** (index 0 or last index).

```bash
PATH="/home/user/"
echo "${PATH#/}"     # Result: "home/user/" (Only if it starts with /)
echo "${PATH%/}"     # Result: "/home/user" (Only if it ends with /)

# Logic: Without the *, Bash checks only the boundary character. 
# It will NOT "reach inside" the string.
```

