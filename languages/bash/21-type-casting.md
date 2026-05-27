# 🟢 Milestone 21: Type Casting [CORE]

### 1. Contextual Interpretation
Bash does not have a "cast" keyword. Instead, it uses **Contextual Interpretation**: a string "becomes" a number only when you place it inside a context that *expects* a number.

```bash
# CONVENTIONAL: String-to-Int
num="10"
res=$(( num + 5 ))          # Logic: Interpreted as 10 + 5

# Logic: The Arithmetic Engine performs a Lexical Scan. If the 
# string looks like a number (Dec/Hex/Oct), it is converted to 
# a 64-bit integer for the calculation.
```

### 2. Explicit Formatting
To "Cast" data for output (e.g., converting a number to a hex string), use the `printf` built-in, which mimics the systems-level C function of the same name.

```bash
# EXPLICIT: Format Casting
val=10
hex_str=$(printf "0x%X" $val) # Logic: Casts 10 to 0xA

# Logic: printf reads the internal integer representation and 
# maps it to a new string format based on the provided specifier.
```
