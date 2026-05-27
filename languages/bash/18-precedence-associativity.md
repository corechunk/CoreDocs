# 🟢 Milestone 18: Precedence & Associativity [CORE]

### 1. Evaluation Order
When an expression contains multiple operators, Precedence determines which action happens first. Bash follows standard C-style precedence rules, but relying on defaults is an anti-pattern.

```bash
# CONVENTIONAL: Linear arithmetic
(( res = 5 + 2 * 3 ))       # Logic: 2*3 happens first -> 11

# EXPLICIT: Forced Priority
(( res = (5 + 2) * 3 ))     # Logic: Addition happens first -> 21

# Logic: The Bash parser builds an Abstract Syntax Tree (AST). 
# Multiplication nodes are placed deeper in the tree than 
# addition nodes, ensuring they are evaluated first.
```

### 2. Logical Precedence
In test contexts, the order of `&&` (AND) and `||` (OR) is critical for short-circuiting logic and error handling.

```bash
# EXPLICIT: Grouped Logic
[[ ($a == "1" || $b == "2") && $c == "3" ]]

# Logic: Parentheses force the parser to evaluate the OR block 
# as a single atomic status before checking the AND condition.
```
