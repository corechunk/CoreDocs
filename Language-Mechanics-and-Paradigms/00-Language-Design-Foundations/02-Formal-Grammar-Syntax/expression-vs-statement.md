# ⚖️ Expression vs. Statement Semantics

## 1. Core Distinction
- **Expression:** Evaluates to a discrete value. (e.g., `5 + 3`, `x > 0`).
- **Statement:** Performs an action or controls execution flow without producing a direct value (e.g., variable assignment, loop execution).

## 2. Paradigm Shift: Expression-Based Languages
Modern systems languages (Rust, Kotlin) treat almost every construct—including `if` conditionals and block scopes `{ ... }`—as value-returning expressions:

```kotlin
val result = if (active) 100 else 0
```
