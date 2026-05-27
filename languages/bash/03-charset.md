# 🔴 Milestone 03: Character Sets (Charset) [SYSTEMS]

### 1. Bytes vs. Characters
A Character Set (Charset) is the map that turns binary numbers (bits) into human-readable symbols. Bash is a "Byte Stream" processor; it doesn't care what the bytes are until it hands them to the terminal.

```bash
# CONVENTIONAL: System-default interpretation
echo "🍎"                   # Displays correctly if locale is set

# VERIFICATION (Memory Layout)
printf "A" | xxd           # 41 (Single byte)
printf "🍎" | xxd          # f09f 8c8e (4 bytes in UTF-8)

# Logic: Bash treats characters as arbitrary byte sequences. 
# Multi-byte characters (like emojis) take up 2-4 slots in memory.
```

### 2. Locale & Encoding Control
The **Locale** is the system configuration that tells Bash how to sort, compare, and display those bytes. UTF-8 is the modern standard for internationalization.

```bash
# EXPLICIT: Environmental Control
export LANG=en_US.UTF-8     # Force UTF-8 interpretation
export LC_ALL=en_US.UTF-8    # Global override

# Logic: Bash relies on the system's C library (libc) to handle 
# charset mapping. These variables tell libc which map to load.
```
