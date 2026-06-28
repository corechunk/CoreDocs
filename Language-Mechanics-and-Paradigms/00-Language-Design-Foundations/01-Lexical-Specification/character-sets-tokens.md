# 🔤 Character Sets, Identifiers, and Token Categories

## 1. Character Encodings & Lexical Streams
Modern compilers ingest source streams encoded in UTF-8. The lexer maps continuous byte streams into atomic token units.

## 2. Token Classification Matrix

| Token Category | Description | Examples |
|---|---|---|
| **Keywords** | Reserved operational identifiers | `var`, `val`, `if`, `else`, `while`, `return`, `struct` |
| **Identifiers** | User-defined names for symbols | `main`, `counter`, `calculate_total` |
| **Literals** | Fixed primitive values | `42`, `3.14159`, `"hello world"`, `true` |
| **Operators** | Mathematical and logical symbols | `+`, `-`, `*`, `/`, `==`, `!=`, `&&` |
| **Delimiters** | Structural block markers | `{`, `}`, `(`, `)`, `;`, `,` |
