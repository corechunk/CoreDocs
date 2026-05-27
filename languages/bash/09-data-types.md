# 🟢 Milestone 09: Data Types [CORE]

### 1. The Typeless Model
Bash is fundamentally "Typeless." Every variable is stored as a character stream (string). If you perform math, the shell "Interprets" the bytes as a number on the fly.

```bash
# CONVENTIONAL: String-based math
num="10"
res=$(( num + 5 ))         # Logic: 10 + 5 = 15

# Logic: When entering an arithmetic context $(( )), Bash scans 
# the string and attempts to convert it to a long integer in 
# temporary memory for the calculation.
```

### 2. Interpretation Flags
To avoid constant re-interpretation, you can set "Attributes" on a variable name. This tells the shell to treat specific names as integers or specialized structures (like arrays) permanently.

```bash
# EXPLICIT: Setting Attributes
declare -i x=10            # Integer flag (forces math context)
declare -a list=(1 2 3)    # Indexed Array flag
declare -A map=([k]=v)     # Associative Map flag
declare -n ref=var         # Nameref flag (The "Pointer")

# BEHAVIOR CHECK
x="string"                 # Logic: x becomes 0 (non-numeric)

# Logic: Attribute-based typing does not change the memory layout 
# (it is still a string), but it changes how the Assignment 
# Engine processes new values for that name.
```

## Deep-Dive Reference
For advanced manipulation and system internals:
- [Parameter Expansion](./data-type/parameter-expansion.md) | [Null Safety & Defaults](./data-type/null-safety.md)
- [Floating Point Limits](./data-type/floating-point.md) | [Attributes & Scoping](./12-scope-lifetime.md)
