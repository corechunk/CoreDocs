# 🟢 Milestone 10: String Escaping [CORE]

### 1. Functional Neutralization
Escaping is the act of stripping a character (like `$`, `"`, or `\`) of its "Magic" or functional role so it can be treated as literal text. This is essential for printing raw symbols or handling complex paths.

```bash
# CONVENTIONAL: Backslash escaping
echo "Total cost: \$5.00"   # Neutralizes the expansion operator

# Logic: The Lexer toggles a "Literal bit" for the NEXT character 
# when it sees a \, causing the parser to ignore its functional 
# meaning and pass the raw byte to the buffer.
```

### 2. Advanced Quoting & Control
For invisible characters (newlines, tabs) or literal blocks, Bash provides specialized quoting engines that handle the heavy lifting.

```bash
# EXPLICIT: ANSI-C Quoting
echo $'Line 1\nLine 2'      # Handle tabs (\t) and newlines (\n)
echo $'\x41'               # Hex code for 'A'

# EXPLICIT: Raw Literal Blocks
echo 'No $VAR expansion'   # Single quotes: Absolute safety

# Logic: $' ' triggers a specialized scan that handles escaped 
# sequences before the string is ever handed to the expansion 
# engine. Single quotes disable the expansion engine entirely.
```

---
*See also: [Terminal Physics & ANSI Escapes](../../OS/Linux/Terminal/ANSI-Escapes.md)*

