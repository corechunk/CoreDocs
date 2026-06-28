# 🔤 Tokenization Mechanics & DFA State Machines

## 1. Regular Expressions to DFAs
The lexical analyzer (lexer/scanner) converts raw source character streams into atomic token units. Tokens are defined using Regular Expressions, which compilers convert into Nondeterministic Finite Automata (NFAs) and then optimize into Deterministic Finite Automata (DFAs).

## 2. The Maximal Munch Principle
When multiple regular expressions match the current input stream, the lexer selects the rule that consumes the longest possible sequence of characters (e.g., `variable_name` is matched as a single identifier, not the keyword `var`).
