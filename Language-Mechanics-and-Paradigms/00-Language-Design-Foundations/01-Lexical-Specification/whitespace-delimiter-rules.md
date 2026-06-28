# 📐 Whitespace and Delimiter Rules

## 1. Delimiter Strategies
Languages handle statement boundaries using either explicit semicolons (C/C++), automatic semicolon insertion (JavaScript/Go), or significant indentation blocks (Python/YAML).

## 2. Significant Whitespace vs. Explicit Blocks
- **Explicit Scoping:** Uses curly braces `{ ... }` to establish lexical scope blocks. Whitespace is ignored.
- **Off-side Rule (Significant Whitespace):** The lexer generates explicit `INDENT` and `DEDENT` tokens based on leading space counts to manage block scope depth.
