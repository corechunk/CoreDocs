# 🟢 Bash: Bitwise Operators [CORE]

### 1. Shift & Mask
Bitwise operations allow you to manipulate data at the bit level inside an arithmetic context `$(( ))`.

```bash
# CONVENTIONAL: Left/Right Shift
x=1
echo $(( x << 2 ))          # Logic: 4 (0001 -> 0100)
echo $(( 8 >> 1 ))          # Logic: 4 (1000 -> 0100)

# Logic: Shifts work on 64-bit signed integers in modern Bash.
```

```bash
# EXPLICIT: Bitwise Logic (AND/OR/XOR/INV)
mask=0x0F
val=0xFF

echo $(( val & mask ))      # Logic: 15 (0x0F)
echo $(( 1 | 2 ))           # Logic: 3
echo $(( 5 ^ 3 ))           # Logic: 6
echo $(( ~1 ))              # Logic: -2 (Two's complement)

# Logic: Bash performs bitwise operations directly on the CPU's 
# integer registers, making it the most efficient way to handle 
# flags and low-level data filters.
```

# The Logic Bridge
// Logic: Bitwise operators in Bash are inherited from C. They operate on the underlying bit representation of the long integer stored in memory. Note that Bash only supports bitwise operations on integers; strings must be converted or interpreted in an arithmetic context first.
