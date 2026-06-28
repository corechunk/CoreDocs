# 🔢 Operator Precedence and Associativity

## 1. Hierarchy Table
Operators with higher precedence bind tighter to operands during AST construction.

| Level | Operator | Description | Associativity |
|---|---|---|---|
| 1 (Highest) | `()`, `[]`, `.` | Call, Index, Member | Left-to-Right |
| 2 | `!`, `-` (unary) | Logical NOT, Unary Minus | Right-to-Left |
| 3 | `*`, `/`, `%` | Multiplicative | Left-to-Right |
| 4 | `+`, `-` | Additive | Left-to-Right |
| 5 (Lowest) | `=` | Assignment | Right-to-Left |

## 2. Applied Data Structure: The Stack
Parsers utilize **Stack data structures** (via Edsger Dijkstra's Shunting-yard algorithm) to convert infix expressions into Abstract Syntax Trees or Reverse Polish Notation (RPN) while honoring precedence.
