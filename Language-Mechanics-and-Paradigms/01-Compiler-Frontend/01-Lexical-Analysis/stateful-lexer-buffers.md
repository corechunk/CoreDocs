# 📦 Stateful Lexer Buffers and Lookahead

## 1. Character Stream Buffering
To process large source files efficiently without excessive I/O system calls, lexers maintain ring buffers or double-buffering schemes in RAM.

## 2. Multi-Character Lookahead & Applied Data Structure (Queues)
When token boundaries depend on upcoming characters (e.g., distinguishing `=` from `==`), the lexer uses lookahead methods.

*   **Data Structure Applied:** Tokens are pushed onto a **Queue data structure** to be consumed asynchronously by the parser downstream.
*   **String Interpolation:** Stateful lexer modes track nested string literal states to handle embedded expression interpolation (e.g., `"Hello ${user.name}"`).
