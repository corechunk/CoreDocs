# 🧹 Whitespace Filtering and Indentation Stacks

## 1. Whitespace Stripping Languages
In languages like C, C++, and Java, non-significant whitespace and comment blocks are discarded by the lexer and do not emit tokens to the parser.

## 2. Off-side Rule & Indentation Tracking
In indentation-sensitive languages (Python, Nim), the lexer maintains an internal **Indentation Stack**:
- When indentation depth increases, it pushes the new depth and emits an `INDENT` token.
- When indentation depth decreases, it pops matching depths and emits `DEDENT` tokens to signal block scope terminations.
