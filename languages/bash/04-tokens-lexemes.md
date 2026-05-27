# 🟢 Milestone 04: Tokens & Lexemes [CORE]

### 1. Whitespace Significance
Tokens are the smallest units Bash understands. In the shell, **Whitespace is a Functional Separator**, not just a formatting choice. Its presence or absence changes the grammar entirely.

```bash
# CONVENTIONAL: Assignment (No spaces)
user="Alice"               # Assignment token

# INCORRECT: Assignment attempt with spaces
# user = "Alice"           # Bash looks for a command named 'user'

# Logic: The Lexer identifies the '=' token immediately followed 
# by text. If spaces exist, the '=' becomes a separate argument.
```

### 2. The Quoting Multiverse
Quoting is how you group multiple words into a single Token and control whether "Magic" characters (like `$`) are expanded or treated as literal text.

```bash
# EXPLICIT: Quoting Modes
echo 'No $user expansion'  # Single Quotes: Raw Literal text
echo "Hello $user"         # Double Quotes: Dynamic Expansion

# EXPLICIT: Multi-word tokens
name="Gemini CLI"          # Spaces are preserved inside quotes

# Logic: Double quotes tell the expansion engine to search for 
# $ markers. Single quotes disable the engine entirely for that block.
```
